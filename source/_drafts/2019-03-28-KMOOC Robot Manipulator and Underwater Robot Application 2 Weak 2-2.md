---
title: "Robot Manipulator and Underwater Robot Application 2주차 2-2 행렬과 벡터의 연산(1)"
strapline: "About Robotics"
description: "RMaURA K-MOOC 강좌 정리"
header:
 overlay_image: /assets/images/triangular.jpeg
categories:
  - "Robotics"
tag:
  - "K-MOOC"
toc: true
toc_sticky: true
last_modified_at: 2019-03-28 
comments: true
mathjax: true
classes: wide
---

서울과학기술대학교 김진현교수님의 K-MOOC강좌 Robot Manipulator and Underwater Robot Application을 공부하고 내용을 정리한 것 입니다.

K-MOOC 강좌 주소: 

<http://www.kmooc.kr/courses/course-v1:SEOULTECHk+SMOOC03k+2019_T3/about>

## 행렬과 벡터의 연산

### 행렬의 덧셈과 곱셈

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (2).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (3).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (4).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (5).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (6).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (7).jpg){% endraw %}|

### 대각합(trace)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2.jpg){% endraw %}|
|*정방행렬의 주대각선 성분들의 합이다.*|

### 행렬식(Determinant)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (8).jpg){% endraw %}|
|*${detA_i}_j$는 minor 행렬 (소행렬식)이다.*|

|{% raw %}![alt](https://wikimedia.org/api/rest_v1/media/math/render/svg/2ae0f49460a5958265eb20c49c2939acc69ebdf8){% endraw %}|

|{% raw %}![alt](https://wikimedia.org/api/rest_v1/media/math/render/svg/5b613b8f479a2740097e90d2d872e738516f3df5){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (9).jpg){% endraw %}|

### 선형 독립, Span, basis

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (10).jpg){% endraw %}|

만약에 k개의 벡터가 존재한다고 했을 때, k개의 벡터들을 각각, 앞에 상수를 전부 다 곱해서, 0으로 만들 수 있는 그런 조합이 존재 한다면 선형종속이라고 한다.

만약 $c_1$~$c_k$까지 전부, 0을 제외하고는 어떤 수를 가지고도 이 전체를 0벡터를 만들 수 없다, 이런 경우를 

‘선형독립’이라고 말합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (11).jpg){% endraw %}|
|*선형독립이 되는 벡터들이 있다면, 어떤 벡터 공간을 만들 수 있게 됩니다.*|

즉, $v_1$~$v_k$까지라고 하는 k개의 어떤 선형독립된 벡터들이 있다면, 그 벡터들을 통해서, 새로운 벡터를 만들어낼 수 있게 됩니다.
이 경우, 이렇게 만드는 과정을 공간을 ‘스팬’한다고 말하게 된다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (12).jpg){% endraw %}|
|*이렇게 3개의 (1, 0, 0), (0, 1, 0), (0, 0, 1)이라고하는 선형독립 벡터를 통해서 공간을 만들어냈을 때, 그 공간을 스팬한다고 말할 수 있다.*|

3차원 벡터를 온전히 스팬하기 위해서, 필요한 최소한의 선형독립 벡터의 수가 3개임을 쉽게 알 수 있습니다.

이 3이라는 숫자가, 바로 차원, 즉 3차원이라고 부르는 차원, 디멘션이라고 말할 수 있습니다.

그리고, 어떤 공간을 만들기 위해서, 필요한 최소한의 수의 벡터를, ‘basis’라고 합니다.

이 basis를 통해서, 전체 벡터 공간을 스팬할 수 있다고 말할 수 있고,	

반대로 그 스팬을 하기 위해 필요한 벡터의 수를 basis, 다른 말로 기저라고 할 수 있습니다.

basis는 

> 기저벡터들은 독립(Independent)이다.

> 기적벡터들은 공간(space)을 "span" 한다.

span자체에서는 column vector가 독립인지 종속인지 상관없다.

### 행렬의 계수(Rank of a Matrix)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (13).jpg){% endraw %}|
|*이러한 선형독립에 대한 이야기를 한 이유는, 바로 행렬의 계수, 즉 랭크라고 부르는 행렬의 계수에 대한 설명을 하기 위해서다.*|

만약에 m by n 매트릭스인 $A$가 있다고 할 때, 굳이 정방행렬일 필요는 없습니다.

이 행렬의 계수는 방금 설명했던 것처럼, 선형 독립적인 칼럼의 수, 선형독립인 로우의 수, 즉 (선형 독립적인) 행과 열의 수가 

바로 랭크가 됩니다

Range space of $A$, 즉 columns으로 만들 수 있는 공간을 뜻하는 $R(A)$의 차원과 같은 개념이 됩니다.

마찬가지로 어떤 매트릭스의 Row Space의 디멘션하고도 같게 됩니다.

만약에 어떤 매트릭스 $A$의 랭크를 구했을 때, 만일 $A$가 옆으로 긴 행렬이면, m by n에서 m이 n보다 작게 됩니다.

이 경우 최대한으로 가질 수 있는 랭크의 수는 이 행의 개수만큼을 초과할 수가 없게 됩니다.

### 역행렬(Inverse Matrix)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (14).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (15).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (16).jpg){% endraw %}|
|*$A$가 nonsingular, 즉 정칙행렬일 경우, 행렬식은 0이 아니고, $A$의 역행렬, $A$의 inverse는 존재합니다.*|

$A$의 inverse 존재할 때, 만약에 $det(A^{-1})$, 즉 역행렬에 대한 Determinant는 $1 \above 1pt detA$의 형태로 구할 수 있습니다.

반대로, Determinant 0이면, 즉 어떠한 매트릭스 $A$의 Determinant이 0일 경우에는 singular 이라고 하고 역행렬의 Determinant은 정의 할 수 없습니다.

역행렬은 어떠한 방법으로 구했건, 한번 구했다면 그 역행렬은 유일합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (17).jpg){% endraw %}|

### 여인수(Cofactor)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (19).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-2 (21).jpg){% endraw %}|
|*역행렬을 범용적으로 구하기위한 수식이다.*|




