---
title: "Robot Manipulator and Underwater Robot Application 3주차 3-2 Single Rigid Body"
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
last_modified_at: 2019-04-04
comments: true
mathjax: true
classes: wide
---

## 강체(Rigid Body)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2.jpg){% endraw %}|
|*동역학, 기구학적 해석을 많이 사용*|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (2).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (3).jpg){% endraw %}|
|*이 2가지를 안다면 물체의 위치와 물체에 대해서 정확하게 설명할 수 있다.*|

변위(Displacement): 나로부터 떨어진 거리, 즉 reference frame(기준틀)이라고 불리는 것부터 떨어져 있는 어떤 object까지의 거리

각도(Attitude or Orientation): 물체가 나를 기준으로 어덯게 틀어져있는지 나타내는 지표

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (4).jpg){% endraw %}|

## Coordinate Frames

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (5).jpg){% endraw %}|

Camera Frame, Tool Frame, Link Frame, Base Frame, Goal Frame, 즉 각각의 좌표들은 내가 어떤 기준점을 가지고 보고 있는지 나타냄

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (6).jpg){% endraw %}|

예를 들면 Camera Frame에서는 카메라의 렌즈를 기준으로 내가 무엇을, 어떤 방식으로 보고 있는지를 나타낸다.

각각의 자기만의 Frame을 가지고 있을 것이고 그 Frame에 맞춰서 Coordinate System에 맞춰서 해석을 하는 게 훨씬 쉬운 일이라는 것을 알 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (7).jpg){% endraw %}|

그렇지만, 일반적으로 카메라에서 보고 있는 것을, 내 기준으로 살펴보거나 로봇의 기준으로 살펴보기 위해서는 각각의 프레임 간의 변형 또는 변환이 필요할 수 있습니다.

## Single Rigid Body Object

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (8).jpg){% endraw %}|

$frame$: 어떤 좌표계에서 $x$,$y$,$z$ 방향의 기준되는 벡터, 단위 벡터가 어떤 식으로 배치되어 있는지를 설명하는 것

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (9).jpg){% endraw %}|

$^\textit{frame}\textbf{p}$: 나는 어느 frame에서 표현된 벡터입니다. 라는 것을 설명하는 표현

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (10).jpg){% endraw %}|

$^\textit{frame}\textbf{v}_\textbf{p}$: frame에 대해서 Point $p$의 속도

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (11).jpg){% endraw %}|

$^\textit{frame1}\textbf{r}_\textit{frame2}$: $frame1$을 기준으로 $frame2$가 어디에 있는지 나타내는 표현

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (12).jpg){% endraw %}|

$^\textit{frame1}\textbf{R}_\textit{frame2}$: $frame1$에 대해서 $frame2$가 얼마만큼 돌아가 있는지 나나태는 표현 (R: Rotation Matrix)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (13).jpg){% endraw %}|

Spatial frame(= reference frame): 절대로 움직이지 않고, 절대로 고정되어 있는 frame

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (14).jpg){% endraw %}|

Body frame: 내가 관심이 있는, 내가 바라봤을 때 움직이고 있는 어떠한 시스템

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (15).jpg){% endraw %}|

$^\textit{frame1}\textbf{v}_\textit{frame2}$: $frame1$에 대해서 $frame2$의 속도

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (16).jpg){% endraw %}|

$^\textit{frame1}\textbf{w}_\textit{frame2}$: $frame1$에 대해서 $frame2$의 각속도

## Kinematic Relationship

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (17).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (18).jpg){% endraw %}|

물체와 나와의 관계를 정확하게 설명하기 위해, 우리는 4X4의 Homogeneous Transformation Matrix라고 불리는, 위에 보이는 이러한 Matrix의 형태로 표현한다.

## Description of a Position

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (19).jpg){% endraw %}|

만약에 어떤 coordinate system상에 존재하는 $P$라는 점이 있다면, 그 $P$라는 점은, $A$라는 어떤 coordinate system이라면, $A$라는 프레임상에서 나의 위치는, $P_x$, $P_y$, $P_z$로, 이러한 Position Vector로서 간단하게 표현이 가능합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (20).jpg){% endraw %}|

그렇다면, $frame0$,$frame1$ 2개의 프레임이 존재하게 되겠고 그 2개의 떨어진 거리는, 지금은 신경쓰지 말고, 지금은 떨어진 거리가 존재하지 않고 일치한다 즉 원점이 일치하도록 위치시킨 다음에. 이들의 어떤 각도가 얼만큼 틀어져있는지만 살펴본다라고 했을 때 우리는 이러한 각도관계를 쉽게 찾아보기 위해서 내적이라는 개념을 쓰면 손쉽게 알아낼 수가 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (21).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (22).jpg){% endraw %}|

이 내적이라는 것은 어떠한 프레임에서 다른 프레임에의 영사, projection 시킴으로서 둘 사이의 관계를 알아낼 수가 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (23).jpg){% endraw %}|

그래서, 위에 보이는 식과 같이, $x$, $y$, $z$를 각각 내적을 취함으로서 이렇게 component 별로 얻어낼 수가 있고, 이것을 보다 더 일반적으로 다시 기술하면, 아래와 같이, 매트릭스의 형태로 표현이 가능합니다.

이렇게 매트릭스 형태로 표현했을 때 즉, 일반 프레임에서의 어떤 $P$점을, 1번 frame에서의 $P$점을, 0번 frame에서 그 $P$점을 어떻게 위치하는 지를 알아내기 위해서 우리는 중간의 이러한 연산관계들을 정리한 Direction cosines의 형태로 Matrix를 곱해줌으로서, 바로 이 $P$점이 1번 프레임이 아닌, 0번 프레임에서 어떻게 설명이 되는지를 알아낼 수가 있게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (24).jpg){% endraw %}|

Orientation은 1번 프레임에서 표현되어 있었던 점을, 0번 프레임으로 가져오기 위해서 변환 관계식을 필요로 한다는 것을 알 수 있겠고 이 변환관계식은 바로 내적이라는 개념을 통해서 뽑아낼 수 있다는 것을 바로 위에서 살펴봤던 식을 통해서 알 수 있게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (25).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (26).jpg){% endraw %}|

2개의 축이 존재할 때, 그 2개의 축을 회전시키면 일치시킬 수 있습니다.
만약에 2개의 축이 $z$축, 즉 $z$축 방향으로 $\theta$만큼 돌아갔을 때, 일치시킬 수 있을때 위에 보이는 식처럼, 이렇게 $cos\theta$와 $sin\theta$,의 관계를 통해서, Rotation Matrix로 표현이 가능합니다.
역시, $x$방향에 대해서도, $y$방향에 대해서도, 각각 Rotation Matrix를 통해서, 2개의 축을 일치시킬 수 있습니다.

2개의 어떤 프레임 상에서의 내적을 통해서, 그 내적을 통해서 만들어낸 Matrix와 어떤 관계를 가지고 있는지, 그 2개는 어떠한 상관관계를 갖고 있는지, 조금 더 살펴볼 필요가 있습니다.

## Rotation

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (27).jpg){% endraw %}|

Rotation이라고 하는 것은 일반적으로 1번 축에서부터 0번 축까지 가지고 오는 회전의 관계 또는 2개의 일치관계를 찾아내는 것이다

이 일치관계를 찾아내는 것을 일반적으로 Rotation Matrix, 즉 1번부터 0번까지 가지고오는 Rotation Matrix로 볼 수도 있고, 또는 2개를 단순히 coordinate trasformation으로 볼 수도 있고 어떠한 한 축에 대한 다른 축, 한 프레임에 대한 다른 프레임에서의 표현법으로 나타낼 수도 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (28).jpg){% endraw %}|

첫 번째로는 보통 1에서부터 0까지 가지고 오는, $R$ Matrix를 1번에서 표현되어 있는 $P$점, 즉 1번 프레임에서 표현되는 $P$점을 0번 프레임으로 mapping시킨다는 개념으로 위에서 보여주는 것처럼, 이러한 Matrix가 주어졌을 때 1번 프레임 상에 놓여 있는 [1,0,0]이라는 점을 $R$이라는 Matrix로 mapping, transformation을 통해서, [0,1,0]으로 mapping
되는 것이라고 생각할 수 있고요.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (29).jpg){% endraw %}|

두번째로는, Rotation을 시킨다는 개념, 즉 (1,0,0)이라고 하는 이 점을 이 Rotation Matrix로 Rotation시키면, 그 다음 프레임에서의 점으로 가지고 올 수 있다, 또는 회전시킬 수 있다, 라는 개념, 즉 Rotation Matrix로 볼 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (30).jpg){% endraw %}|

세번째로는, 1번 프레임에서의 기준 좌표가 0번 프레임에서 어떻게 표현되는지, 즉 1번 프레임에서 2개의 좌표를 보면,
1번 프레임에서 [1,0,0], [0,1,0], [0,0,1]이라고 하는 3개의 기준 좌표를, 0번 좌표계에서 표현하게 되면, [0,1,0], [-1,0,0], [0,0,1]로 각각의 좌표계를 표현할 수 있게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (31).jpg){% endraw %}|

## Rotational Matrices

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (32).jpg){% endraw %}|

이러한 Rotation Matrix는 special orthogonal group, 즉 $SO(3)$라고 하는 그룹에 포함되어 있다고 설명을 할 수 있겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (33).jpg){% endraw %}|

special orthogonal group이라는 것은 그 그룹에 포합된 벡터들이 상호간에는 orthogonal, 즉 내적을 취했을 때 0이 되고 자기 자신을 내적했을 때에는 크기가 1이 되는 성질을 가지고 있는 그러한 벡터들의 집합을 보통 special orthogonal group이라고 말합니다.
그 중에서, 삼차원 벡터 3개로 이루어진 집합을 special orthogonal group(3)이라고 표현합니다.
이러한 special orthogonal group에 포함되어 있는, 벡터들의 집합이 매트릭스를 이루고 이를 $R$이라고 했을 때,
R에 대한 역행렬을 구할 때 자기 자신을 Transpose한 것을 가지고 곱하게 되면 역행렬을 얻을 수 있고 Determinant를 했을 때, 1이 나온다는 좋은 성질들을 가지고 있습니다.

이러한 성질들은 추후에 어떤 연산을 진행할 때, 편하게 연산이 진행될 수 있기 때문에, 연산들의 특징을 가지고 있는 Rotation Matrix는 special orthogonal group에 포함되어 있는 Matrix 라고 알아두면 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (34).jpg){% endraw %}|

Rotation Matrix의 조금 전에 말했던 special orthogonal group(3)에 포함되어 있는 성질들 때문에 Rotation Matrix는 3X3 Matrix이기 때문에, 9개의  variable로 이루어져 있는데 그 중에서, 각각의 벡터들끼리는 서로 직교한다는 성질 3가지,
즉 $R_1$, $R_2$, $R_3$가 $R_1$과 $R_2$, $R_1$과 $R_3$, $R_2$와 $R_3$가 서로 직교한다는 성질 3가지,
그리고 $R_1$의 크기는 1, $R_2$의 크기는 1, $R_3$의 크기는 1, 이라고 하는 3가지,
즉 6가지의 constraints를 가지고 있기 때문에, 총 9개의 variable이지만, 3개의 parameter만 독립인 매트릭스가 되겠습니다.

좌표계가 공간 상에서 3개의 각도를 가진다, 라는 개념과 동일합니다.
즉 3개의 각도를 가진다는 개념과 동일하게 생각할 수 있어 역시 Rotaion Matrix에서도, 3가지의 parameter만 서로 독립인 그러한 성질을 갖게 됩니다.

이러한 로테이션 매트릭스는 우리한테 이것들이 commute하지 않는다는 어려움을 줍니다.

즉 내가 Rotation을 어느 방향으로 먼저 하느냐에 따라서 이 순서를 지키지 않으면, 엉뚱한 결과가 나올 수 있는, 즉 commute하지 않다는 성질들 때문에 직관적이지 않다는 측면 때문에 많은 사람들이 어려움을 갖습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (35).jpg){% endraw %}|

이러한 Rotation Matrix는 어떻게 표현하느냐에 따라서 여러가지 이름으로 불리고 있습니다.
대표적으로 비행기의 어떤 자세각도를 표현하기 위해서, Roll, Pitch, yaw라는 angles을 통해서 설명하기도 하고,
그리고 로봇에서 범용적으로 널리 사용되는 것은 Euler Angle이라는 방법 입니다.

Euler Angle의 parameters들을 활용해서 Quaternions이라는 개념을 통해서 각도를 기술할 수도 있습니다.
또는, Rodrigues parameters라는 Gibbs vectors를 활용해서 표현하는 기법도 있고,
이 Rodrigues parameters가 표현하기가 어렵기 때문에 Modified Rodrigues parameters로 표현하는 경우도 있습니다.


|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (36).jpg){% endraw %}|

조금 전에 말했던 것처럼 각도를 표현하는 데에 있어서 어려움이 있는 이유는 일반적으로 로테이션은 commute하지 않기 때문입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (37).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (38).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (39).jpg){% endraw %}|

먼저 $x$방향으로 먼저 돌리고 $z$축방향으로 돌렸을 때, 나타나는 위에 보이는 그림에서의 책이 마지막에 이렇게 서 있는 모습과
반대로 $z$축으로 먼저 돌리고 $x$축으로 돌렸을 때, 서 있는 그림은 다르다는 것을 알 수가 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (40).jpg){% endraw %}|

여러분들이 길을 찾아갈 때, 어떤 블록에서 좌회전을 먼저 하고 우회전을 하는 것과 우회전을 먼저 하고 좌회전을 했을 경우에, 여러분들이 최종적으로 위치하게 되는 지점은 다르다는 것을 쉽게 이해할 수 있을 겁니다. 즉 이러한 Rotation은 어떻게 회전하느냐에 따라서 다른 결과를 내기 때문에, 생각하는 데에 있어서, 조심할 필요가 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-2 (41).jpg){% endraw %}|

반면에, 위치 같은 경우에는 $x$방향으로 얼마만큼 가고 $y$방향으로 얼마만큼 갔을 때와 $y$방향으로 먼저 가고 $x$방향으로 갔을 때의 그 두 위치는 같다라는 것을 알 수 있습니다. 그 두 가지의 차이에 의해서, 위치와 각도에 대한 생각의 방향들을 달리해볼 필요가 있을 것입니다.














