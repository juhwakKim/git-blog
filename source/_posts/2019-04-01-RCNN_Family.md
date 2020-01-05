---
title: "RCNN Family 간단 정리"
date: 2019/4/1
categories:
  - "theory"
tag:
  - "deep learning"

updated: 2019-08-07
comments: true
mathjax: true

---

## R-CNN

### Region Proposals

![alt](/images/Deep-learning/etc/R-CNN_F.png)

입력 영상에서 ‘물체가 있을 법한’ 영역을 빠른 속도로 찾아내는 알고리즘을 region proposal 알고리즘이라 합니다. 

ex) Selective search, Edge boxes

### Transfer Learning

기존의 만들어진 모델을 사용하여 새로운 모델을 만들시 학습을 빠르게 하며, 예측을 더 높이는 방법입니다.

사용되는 이유:
> 1. 실질적으로 Convolution network을 처음부터 학습시키는 일은 많지 않습니다. 대부분의 문제는 이미 학습된 모델을 사용해서 문제를 해결할 수 있습니다.
> 2. 복잡한 모델일수록 학습시키기 어렵습니다. 어떤 모델은 2주정도 걸릴수 있으며, 비싼 GPU 여러대를 사용하기도 합니다.
> 3. layers의 갯수, activation, hyper parameters등등 고려해야 할 사항들이 많으며, 실질적으로 처음부터 학습시키려면 많은 시도가 필요합니다.

결론적으로 이미 잘 훈련된 모델이 있고, 특히 해당 모델과 유사한 문제를 해결시 transfer learining을 사용합니다.

#### 새로 훈련할 데이터가 적지만 original 데이터와 유사할 경우
데이터의 양이 적어 fine-tune (전체 모델에 대해서 backpropagation을 진행하는 것) 은 over-fitting의 위험이 있기에 하지 않습니다. 
새로 학습할 데이터는 original 데이터와 유사하기 때문에 이 경우 최종 linear classfier 레이어만 학습을 합니다.

#### 새로 훈련할 데이터가 매우 많으며 original 데이터와 유사할 경우
새로 학습할 데이터의 양이 많다는 것은 over-fitting의 위험이 낮다는 뜻이므로, 전체 레이어에 대해서 fine-tune을 합니다.

#### 새로 훈련할 데이터가 적으며 original 데이터와 다른 경우
데이터의 양이 적기 때문에 최종 단계의 linear classifier 레이어를 학습하는 것이 좋을 것입니다. 반면서 데이터가 서로 다르기 때문에 거의 마지막부분 (the top of the network)만 학습하는 것은 좋지 않습니다. 서로 상충이 되는데.. 이 경우에는 네트워크 초기 부분 어딘가 activation 이후에 특정 레이어를 학습시키는게 좋습니다.

#### 새로 훈련할 데이터가 많지만 original 데이터와와 다른 경우
데이터가 많기 때문에 아예 새로운 ConvNet을 만들수도 있지만, 실적적으로 transfer learning이 더 효율이 좋습니다. 전체 네트워크에 대해서 fine-tune을 해도 됩니다.

<https://fabj.tistory.com/57>

### R-CNN의 구조

![alt](/images/Deep-learning/etc/R-CNN_F_(2).png)

> 1. 이미지를 입력으로 받음
> 2. Selective search를 이용해 이미지로부터 약 2000개 가량의 region proposal을 추출함
> 3. 각 region proposal 영역을 이미지로부터 잘라내고(cropping) 동일한 크기로 만든 후(warping), CNN을 활용해 feature 추출
> 4. 각 region proposal feature에 대한 classification을 수행

> 1. ImageNet classification 데이터로 ConvNet을 pre-train 시켜 모델 $M$을 얻습니다.
> 2. $M$을 기반으로, object detection 데이터로 ConvNet을 fine-tune 시킨 모델 $M^\'$을 얻습니다.
> 3. object detection 데이터 각각의 이미지에 존재하는 모든 region proposal들에 대해 모델 $M^\'$으로 feature vector $F$를 추출하여 저장합니다.
> 4. 
    >a. 추출된 $F$를 기반으로 classifier (SVM)을 학습합니다.
    >b. 추출된 $F$를 기반으로 linear bounding-box regressor를 학습합니다.

여기서 CNN은 Transfer Learning을 사용

4. :모델의 마지막 층에 SVM을 두어 간단하게 이 결과가 객체인지 아니지, 객체가 맞다면 어떤 객체인지를 분류하도록 하였다.

**문제점**

**localization에 취약함**

**-> 개선: linear regression model을 통해 tight하게 맞추도록함** [참고](https://nittaku.tistory.com/273)

모델이 Image feature를 생성하는 것(CNN), classifier가 class를 예측하는 것(SVM), regression model이 bouding box를 찾아낸 것 (linear regression) 총 3개가 필요합니다.

### R-CNN의 단점

> 1. Test 속도가 느림(CNN을 2000번 돌리기 때문)
> 2. 학습과정이 복잡함(3단계 pipeline)
> 3. Input image 크기를 강제로 224 x 224로 warp, crop

## Fast R-CNN

### SPP(Spatial Pyramid Pooling)

![alt](/images/Deep-learning/etc/R-CNN_F_(3).png)

다양한 크기의 입력으로부터 일정한 크기의 feature를 추출해 낼 수 있는 방법 중 Bag-of-words (BoW)라는 방법이 있습니다. 하지만  BoW는 이미지가 지닌 특징들의 위치 정보를 모두 잃어버린다는 단점이 존재합니다.

![alt](/images/Deep-learning/etc/R-CNN_F_(4).png)

이러한 단점을 보완하기 위한 Spatial Pyramid Pooling 은 이미지를 여러개의 일정 개수의 지역으로 나눈 뒤, 각 지역에 BoW를 적용하여 지역적인 정보를 어느정도 유지할 수 있게 됩니다.

### ROI Pooling(Single-level SPP)

![alt](/images/Deep-learning/etc/R-CNN_F_(5).png)

SPP layer는 feature map 상의 특정 영역에 대해 일정한 고정된 개수의 bin으로 영역을 나눈 뒤, 각 bin에 대해 max pooling 또는 average pooling을 취함으로써 고정된 길이의 feature vector를 가져올 수 있습니다. Fast R-CNN에서는 이러한 SPP layer의 single level pyramid만을 사용하며, 이를 RoI Pooling layer라고 명칭하였습니다.




![alt](/images/Deep-learning/etc/R-CNN_F.gif)

RoIPool의 핵심은 한 이미지의 subregion에 대한 forward pass값을 서로 공유하는 것이다. 위의 그림을 통해 어떻게 각 region에 대한 CNN feature가 feature map의 동일한 영역으로 부터 선택되어 값을 얻어내는지 확인할 수 있습니다.

### Fast R-CNN의 구조

![alt](/images/Deep-learning/etc/R-CNN_F_(6).png)

![alt](/images/Deep-learning/etc/R-CNN_F_(7).png)

> 1. pretrained된 모델에 이미지를 1개만 입력으로 받음
> 2. CNN을 통과한 feature map을 selective search로 2000개 가량의 region proposal을 추출함
> 3. region proposal(feature map)을 Roi pooling을 한다.
> 4. Softmax classifier와 linear bounding-box regressor의 loss를 더하여 학습시킨다.

특징: CNN을 2000번 돌리는 것이 아닌 1번만 돌리면 된다.(속도 향상), 모델이 3개에서 1개의 네트워크로 통일됨

### Fast R-CNN의 장단점

#### 장점
> R-CNN에 비해 detection/localization 정확성 및 속도 개선

#### 단점
> region proposal 시간을 포함 시 real-time X (region proposal 에서 병목 현상)

## Faster R-CNN

### RPN(Region Proposal Network)

Fast R-CNN 중 Selective Search(Region proposal)부분을 딥러닝으로 바꾼 것을 RPN이라 한다. 즉, 이 CNN기반의 미니 CNN인 RPN이 

이미지 -> CNN -> output feature(feature map)를 잘라준다.

RPN의 Covolution NN이 output feature를 sliding window방식으로 돌면서 연산후 classification 과 Regression 연산까지 한다.

forward/ backward propagation -> weight 업데이트 과정을 거치면 -> Selective search를 대체하여 이미지를 2000개로 조각낸다. 즉, CNN기반의 RPN이 sliding window방식으로 box를 찾는 역활을 한다.

![alt](/images/Deep-learning/etc/R-CNN_F_(8).png)

#### RPN 구현 방법

> 1. 이미지를 CNN으로 연산한다.
> 2. 연산 결과를 n x n(보통 3x3) Convolutional Layer로 연산하고, 이 연산 결과가 맞는지를 보유하고 있는 bounding box 데이터와 Loss Function으로 비교한다.
> 3. Loss function 결과로 backpropagation을 시키면 Region Proposal Network가 학습된다.

이 때, box를 찾는 과정에서, 어떤 object는 가로가 길고, 어떤 object는 세로가 길어서, sliding window가 꼭 정사각형이 아니라 직사각형 형태로 도는 것이 유리할 수 있다. 이러한 여러 형태의 sliding window를 anchor box라 한다.

그래서 RPN에서는 output feature인 feature map을 도는 여러개의 anchor box를 운영한다. 즉 CNN의 필터 대신, RPN은 anchor box를 사용하여, 따로 foward/backward하면서 training하여, 2000조각 낼 부분을 predict한다.

### Faster R-CNN구조

> 1. image를 CNN에 집어넣는다.
> 2. CNN에서 나온 output feature(feature map)을 RPN에 집어넣어 classification 과 box를 얼마나 쳐야하는지를 따로 return받는다.
> 3. Roi pooling을 이용하여 box크기를 fully-connected에 넣을 수 있게 resizing해준다.
> 4. fast R-CNN과 동일하게 해준다. 1개의 모델에 끝에만 classification / regression을 따로 만들어 loss2개, weight업데이트도 2개로 따로하여 classification / regression(box위치)를 predict한다.


##TODO

Mask R-CNN정리
## 참고

<http://incredible.ai/artificial-intelligence/2017/05/13/Transfer-Learning/>

<https://blog.lunit.io/2017/06/01/r-cnns-tutorial/>

<https://junn.in/archives/2517>

<https://nittaku.tistory.com/273>
