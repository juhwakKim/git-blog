---
title: "[CVPR 2017] Realtime Multi-Person 2D Pose Estimation using Part Affinity Fields 리뷰"
date: 2019/8/2
categories:
  - "paper"
tags:
  - "deep_learning"
toc_sticky: true
updated: 2019-08-07
comments: true
mathjax: true
---

[Realtime Multi-Person 2D Pose Estimation using Part Affinity Fields](https://arxiv.org/abs/1611.08050)을 읽고 정리한 글입니다.

## Introduction

Human pose estimation 문제는 다음과 같은 어려움 점이 존재합니다.

### Challenges

1. **Unknown number of people that can occur in a frame. (한프레임에 사람에 몇명이 있는지 모른다.)**
2. **Complex Spatial Interference - Contact, Occlusion between people. (사람들간의 접촉, 맞물림등 복잡한 공간적 간섭이 존재)**
3. **Variance in person scales (사람들의 크기가 다양함)**
4. **Run time Complexity. (실행시간이 길다)**

Human pose estimation 문제를 접근하는 방법을 크게 Top-down Approach, Bottom-up Approach 두가지 방법이 있습니다.

### Top-down Approach

![openpose](/images/Deep-learning/Openpose/Openpose_paper.png "openpose paper")
>**Fig1. Top-down Appraoch방식은 이미지에서 사람을 먼저 찾고 관절을 추정하는 방식입니다.**

#### Problem 

* Human detector가 사람을 잘못찾으면 이를 해결할 방법이 없다.
* 사람의 수가 많아지면 computational cost가 증가한다. (<span style="color:red"> Challenges 4 </span>)

### Bottom-up Approach

![openpose](/images/Deep-learning/Openpose/Openpose_paper(2).png "openpose paper")
>**Fig2. Bottom-up Appraoch방식은 관절을 먼저 다찾고 이를 알맞게 이어주는 방식입니다.**

#### Problem

* **찾은 관절을 매칭할 수 있는 조합이 매우 많고 이를 적절하게 매칭하는데 시간이 많이 걸리고 Accuracy도 높이는 것이 힘듭니다.**

## Architecture

![openpose](/images/Deep-learning/Openpose/Openpose_paper(3).png "openpose paper")
>**Fig3**

![openpose](/images/Deep-learning/Openpose/Openpose_paper(4).png "openpose paper")
>**Fig4**

### Input & 2 Branch

**Input: RGB color image**

* **병렬적으로 구성된 2개의 Branch**
    * **Branch 1에서는 Confidnce maps를 찾아낸다. 
    $$S^1 = \rho^1(F), S^t = \rho(F,S^(t-1),L^(t-1), \forall t \ge 2) - (1)$$**
    * **Branch 2에서는 PAF를 찾아낸다. 
    $$S^1 = \rho^1(F), S^t = \rho(F,S^(t-1),L^(t-1), \forall t \ge 2) - (2)$$**


* **$S^t$:$\ \$ Stage $t$에서 만들어진 Confidence maps**
* **$F$:$\ \$  VGG-19에서 추출된 Feature**
* **$L^t$:$\ \$  Stage $t$에서 만들어진 PAF**

![openpose](/images/Deep-learning/Openpose/Openpose_paper(5).png "openpose paper")
>**Fig5.stage가 지날수록 성능이 향상된다.**
>**(위에 주황색원: False negative, 빨간원: False positive이 해결되고 있음**

### Loss function

groundtruths와 추정된 값의 $L_2$ loss를 사용하였다.

**$$f_{S}^t = \sum\limits_{j=1}^J\sum_{p}W(p) \dot \lVert S_{j}^t(p) - S_{j}^{\ast}(p)\rVert_{2}^2   - (3)$$**

**$$f_{L}^t = \sum\limits_{c=1}^C\sum_{p}W(p) \dot \lVert L_{c}^t(p) - L_{c}^{\ast}(p)\rVert_{2}^2   - (4)$$**


* **$J$,$C$:  Confidence map의 개수와 PAF의 개수**
* **$f_{S}^t$:  Stage $t$ 에서의 Confidence map loss**
* **$f_{L}^t$:  Stage $t$ 에서의 PAF loss**
* **$p$:  이미지의 좌표**
* **$W(p)$:  binary mask, true-positive를 처벌하는것을 피하기위해서 사용됨, annotation이 없을때 $W(p) = 0$**

Stage 마다 loss를 계산하여 Vanishing gradient를 해결(<span style="color:red"> [paper](https://arxiv.org/abs/1602.00134)</span>)

### overall objective

**$$f = \sum\limits_{t=1}^T(f_{S}^t + f_{L}^t)- (5)$$**

## Generation of confidence map

dataset은 keypoint만 주어지기에 groundtruths에 될 confidence maps를 만들어 줘야한다.

**$$S_{j,k}^{\ast}(p) =  \exp (-\dfrac{\lVert p-x_{j,k}\rVert _{2}^2}{\sigma^2}) - (6)$$**
* **$S_{j,k}^{\ast}(p)$:$ \ \ k$번째 사람의 $j$번째 관절의 confidence map**
* **$x_{j,k}$:$\ \ k$번째 사람의 $j$번째 관절의 keypoint**
* **$\sigma$:$ \ \$ peak의 범위를 조절함**

![openpose](/images/Deep-learning/Openpose/Openpose_paper(6).png "openpose paper")

>Fig6. 

**$$S_{j}^{\ast}(p) = \max_{\rm k}S_{j,k}^{\ast}(p) - (7)$$**

이렇게 만든 가우시안 분포에 max를 취해준다.(average보다 peaks가 distinct하게 남아서 근접에 대한 정밀도를 가진다.)

## PAFs(Part Affinity Fields)

![openpose](/images/Deep-learning/Openpose/Openpose_paper(7).png "openpose paper")
>**Fig7.** 

* **(a):$ \ \$ keypoint의 모든 연결 후보,**
* **(b):$ \ \$ 각 연결 쌍의 중간점을 추가하여 중간 점의 발생률을 가지고 그리기(초록색선:틀린선,검은선:맞는선), 
사람들이 몰려있으면 오판될 수 있다.
(이러한 방법은 위치만 고려하고 방향은 고려 하지 않고 region of support of limb를 한점으로 줄여버린다.)**
* **(c):$ \ \$PAF를 이용한 결과(위치와 방향문제 해결 및 region of support of limb의 문제를 해결)**

![openpose](/images/Deep-learning/Openpose/Openpose_paper(8).png "openpose paper")
>**Fig8.**

식(4)를 풀기위해서 train때 PAF의 groundtruth를 다음과 같이 정의합니다.
**$$L_{c,k}^{\ast}(p) = \begin{cases}
v & \ \ \text{ if } \ p \ \text{on limb} \ c,k \cr
0 & \ \ \  \text{otherwise.}
\end{cases} - (8) $$** 

* **$c$:$\ \$limb의 종류**
* **$v$:$\ \ v = \frac{(x_{j_2,k}-x_{j_1,k})}{\lVert x_{j_2,k}-x_{j_1,k}\rVert_2}$, limb의 방향의 unit vector(위 그림의 초록색선)**

limb위에 있는 points는 distance threshold내로 정의합니다.

**$$0 \le v \dot (p-x_{j_1,k}) \le l_{c,k}  \, \text{and} \, \|v_{\perp} \dot (p-x_{j_1,k})\| \le \sigma_l - (9)$$**

* **$l_{c,k}$: $\ \ l_{c,k} = \lVert x_{j_2,k} - x_{j_1,k}\rVert_2$, limb의 길이**
* **$\sigma_l$:$ \ \$ limb의 폭**

마지막으로 이미지에 모든 사람으로 평균화 합니다.

**$$L_{c}^{\ast}(p) = \dfrac 1 n_{c}(p) \sum_{k}L_{c,k}^*(p)  - (10)$$**

* **$n_c(p)$:$\ \$p에서의 non-zero vectors의 수(서로다른 사람의 limbs의 overlap되는 픽셀을 평균화시킴)**

test때 에는 $d_{j_1}$으로부터 $d_{j_2}$로 일정간격으로 선적분을 수행하여 affinity field의 세기(E)를 구합니다.

**$$E = \int_{u=0}^{u=1} L_c(p(u)) \cdot \dfrac {d_{j_2}-d_{j_1}} {\lVert d_{j_2}-d_{j_1} \rVert_2} du - (11)$$**

* **$L_c$: $ \ \$예측된 PAF**
* **$d_{j_1}$: $ \ \$  시작part 위치**
* **$d_{j_2}$: $ \ \$  끝 part 위치**
* **$p(u)$: $ \ \$  $p(u) = (1-u)d_{j_1} + ud_{j_2}$, 2 part의 위치 사이를 채웁니다.**

## Multi-Person parsing using PAFs

![openpose](/images/Deep-learning/Openpose/Openpose_paper(9).png "openpose paper")

>**Fig9 (a): Original image (b): 가능한 모든 연결 (c): 사람의 관절구조(spanning tree형태) (d): 이웃한 관절끼리 두개씩의 매칭**

non-maximum suppression(NMS)을 사용해서 모든 part의 confidence maps를 구하였습니다.

이로인해 다양한 후보가 발생하고 여러 사람이 있기에 false positive 문제가 발생할 수 있습니다.

optimal한 parse를 찾는 문제는 K-dimensional matching problem을 가지고있다.(NP-Hard 이라고도 함) 

이 논문에서는 계속해서 high-quality한 match를 찾는 greedy relaxation을 말하고 있습니다.(optimal association 문제를 maximum weight bipartite graph
matching problem으로 줄입니다.)

어떠한 2개의 edge도 1개의 node를 공유하지 않기에 목표는 주어진 edges에서 maximum weight를 찾는 것입니다.(weight는 식(10)을 이용하여 구합니다)

**$$\max_{Z_c}E_c = \max_{Z_c} \sum_{m \in D_{j_1}}\sum_{n \in D_{j_2}}E_{mn}\dot z_{j_1j_2}^{mn} - (12)$$**

* **$z_{j_1j_2}^{mn}$:$\ \ z_{j_1j_2}^{mn} \in \lbrace 0,1\rbrace$, detection candidates $d_{j_1]}^m$와 $d_{j_2}^n$이 연결되 있는지 아닌지를 나타내는 변수**

* **$Z$:$\ \ Z = \lbrace z_{j_1j_2}^{mn} \text{for} j_1,j_2 \in \lbrace 1...J\rbrace,m\in \lbrace 1...N_{j_1}\rbrace,n \in \lbrace 1...N_{j_2}\rbrace\rbrace$, $z_{j_1j_2}^{mn}$ 가능한 모든 연결의 집합**

* **$D_J$:$\ \ D_J = \lbrace d_j^m : \text{for}  j \in \lbrace 1...J\rbrace,m\in \lbrace 1...N_j\rbrace\rbrace$,body part detection candidates의 집합**

결론적으로 optimization은 다음과 같이 표현된다

**$$\max_{Z} E = \sum_{c=1}^C\max_{Z_c}E_c - (13)$$**

(<span style="color:blue"> ? adjacent tree nodes는 PAFs에의해서 explicitly 하게 모델되었고 nonadjacent tree nodes는 CNN에의해 implicitly 모델되었습니다. </span>)

(<span style="color:blue"> ? 이러한 특성은 CNN이 large receptive field를 가지고 train 되고 non-adjacent tree nodes의 PAFs 또한 predicted PAF에 영향 끼쳤기에 발생하였습니다. </span>)

## Results

### MPII Multi-person Dataset

![openpose](/images/Deep-learning/Openpose/Openpose_paper(10).png "openpose paper")

### COCO Dataset

![openpose](/images/Deep-learning/Openpose/Openpose_paper(11).png "openpose paper")

![openpose](/images/Deep-learning/Openpose/Openpose_paper(12).png "openpose paper")

## Reference

https://ml.starall.kr/1

https://cloudup.com/i_gPL3kASQg