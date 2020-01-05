---
title: "Robot Manipulator and Underwater Robot Application 3주차 3-5 Homogeneous Transformation"
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
last_modified_at: 2019-04-07
comments: true
mathjax: true
classes: wide
---

## Homogeneous Transformation

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5.jpg){% endraw %}|

Homogeneous Transformation이라고 하는 것은 어떠한 2개의 좌표계 사이의 2번째 좌표계에 있는 한 점, $P$라는 그 점을 1번째 좌표계에 있는 점으로서 1번째 좌표계에서 표현하는 방법을 나타낼 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (2).jpg){% endraw %}|

위의 그림에서 보이는 것처럼, B라는 프레임에서의 한 점 P가 존재하는 데 이 B라는 프레임에서 점 P라는 부분을 A라는 프레임에서 살펴보고 싶다는 것이죠.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (3).jpg){% endraw %}|

예를 들면 여러분들은 지구에 있고 지구에서 달에 있는 한 점의 위치를 알고 싶을 때, 그 점에 대해 정확히 알기 위해서는 여러분들은 지금 여기 서 있는 지점에서 달의 중심까지의 거리(좌표)와 그 달에서 점까지 위치, 그 2개의 벡터를 가지고 설명한다면 조금 더 쉽게 그 점을 표현할 수 있을 겁니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (4).jpg){% endraw %}|

마찬가지로, 어떠한 B라는 프레임 위의 점을 설명하기 위해서 B라는 프레임에서의 점을 A라는 프레임에서 어떻게 설명되는지 프레임을 돌리는 로테이션시켜서 A라는 프레임에 대해서 설명하는 방법, 그 B라는 프레임에서의 P점을 A로 가지고 오는 로테이션 매트릭스
즉 로테이션 매트릭스 B from A 라고 하는 $ARB$라는 것을 통해서 이 B라는 프레임에서의 P점의 위치를 설명할 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (5).jpg){% endraw %}|

그 위치를 설명한 내용에다 추가를 해서 B라는 프레임에서의 기준점 그 원점을 A라는 프레임에서 설명하는, 즉 B의 origin을 A에 대해서 설명한 위치 이 2가지로 설명할 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (6).jpg){% endraw %}|

이렇게 설명하는 것이 바로 위의 식처럼 A라는 프레임에서의 P점은 B라는 프레임에서의 P점을 가지고 옮겨오는 이러한 수식으로서 표현이 가능합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (7).jpg){% endraw %}|

이렇게 설명되어있는 것을 4차원으로 확장해보도록 하겠습니다.

먼저, 이 Position vector에다가는 1이라고 하는 이 숫자를 더함으로서 원래 Position vector는 3X1벡터가 되는데 이를 4X1의 벡터의 형태로 바꾸게 됩니다.
그 다음에, Transposition Matrix라는 부분을 4 by 4 매트릭스로 확장하게 되는데, 이 4 by 4 매트릭스 같은 경우에는 앞의 3 by 3 부분은 Rotation Matrix를 배치하고 그 옆의 3 by 1벡터는 B의 origin에서부터 A까지, 즉 A프레임에 대한 B origin의 좌표를 배치하고 아랫쪽에는 [0,0,0,1]이라는 4가지 숫자를 배치함으로서, 4 by 4 매트릭스로 확장하게 됩니다.

여러분이 이 식을 매트릭스의 연산을 배웠기 때문에 이 매트릭스의 연산을 계산해보면, 즉 $A^p$, A프레임에 대한 P점은 Rotation Matrix*P, B프레임에 대한 P와, P점인데, 이 P점은 A프레임에 대한 origin*1을 하기 때문에 결과적으로, 위에 표현되는 식은 앞서서 설명했던 이 위에 있는 식, 즉 P가 A에서 어떻게 기술되는지를, 즉 B의 origin과 Rotation Matrix를 통해서 설명한 이 식과 정확하게 일치하는 것을 확인할 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (8).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (9).jpg){% endraw %}|

위에 있는 식은 분명히 Rotation Matrix에 $p$라는 포지션 벡터를 곱하고 그에 다시 origin이라는 position vector를 더해주어 얻어지는 즉 곱하기와 더하기로 이루어진 연산이었는데
밑의 식은 이러한 4 by 4 매트릭스로 확장하는 하나의 매트릭스에 벡터 하나를 곱하기 한번의 연산으로 바꿔주기 때문에 내부적으로 똑같지만 우리의 생각은 단순해질 수 있죠.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (10).jpg){% endraw %}|

수식적으로는 똑같지만 생각에 있어서는 곱하고 더하는 과정을 단순하게 하나의 곱하기로 바꾸어서 대체해서 생각할 수 있다는 장점을 가질 수 있기 때문에
이렇게 Homogeneous Transformation이라고 부르는 것을 4 by 4 매트릭스를 도입하게 된 것입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (11).jpg){% endraw %}|

더 나아가서, 이러한 Homogeneous Transformation의 의미를 좀 더 살펴볼 필요가 있는데 이 Homogeneous Transformation을 T라고 표현할 때 위의 3 by 3, 일반적으로 Rotation Matrix, 두 좌표계 상의 로테이션을 각도를 맞춰주는 로테이션을 의미하고
그 옆에 있는 Translation Vector 같은 경우에는 두 좌표계 사이의 원점 사이의 거리 Vector를 의미하게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (12).jpg){% endraw %}|

추가적으로, 밑에는 아까 [0,0,0,1]이라고 말씀드렸는데, 로보틱스나 일반적인 트랜스포메이션 매트릭스에서는 항상 밑에는 [0,0,0,1]이라는 개념을 활용해서 쓸 텐데
이것들이 꼭 [0,0,0,1]로만 고정되는 것은 아닙니다.

컴퓨터 그래픽스나 캐드 툴 등에서 사용할 때, 한쪽으로 확장시킨다거나 Zoom out/In을 할 때에는
바로 이러한 밑의 Perspective Translation과 scaling vector 등을 활용해서, zooming이나 한쪽으로만 비대칭적으로 더 확장할 때,
이러한 개념으로서의 확장을 할 수 있는 여지도 밑의 4개의 항들로 구현이 가능하기 때문에 Homogeneous Transformation의 매트릭스, T는 굉장히 다양한 분야에서 널리 쓰일 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (13).jpg){% endraw %}|

그렇지만, 이 로보틱스 분야와 기구학 분야에서는 Perspective Translation에서는 [0,0,0]로, Scaling Factor는 1로 고정하는 그런 매트릭스로 활용할 예정입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (14).jpg){% endraw %}|

추가적으로, Homogeneous Transformation을 앞서서 살펴본 것처럼 이렇게 3 by 1 벡터는 3 by 3 매트릭스*3 by 1 벡터를 하고 3 by 1 벡터를 더해주는 과정을, 4 by 1 백터는 4 by 4 매트릭스에 4 by 1 벡터를 곱해주는
이러한 Homogeneous Transformation으로 바꿀 수 있는 방법에 대해서 말씀드렸습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (15).jpg){% endraw %}|

이렇게 A라는 프레임과 B라는 프레임이 있고 B라는 프레임의 한 점 [0,1,1]이라는 점이 있고 이 B라는 프레임은 A와 비교해서 로테이션이 이루어져 있습니다. 그리고 B라는 프레임에서의 원점은 A라는 프레임에 대해서 [0,3,1]만큼 떨어져 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (16).jpg){% endraw %}|

그렇다면, B라는 프레임에 있는 [0,1,1]이라는 점을, Homogeneous Transformation에서 Rotation Matrix를 먼저 정의할 필요가 있는데 여기서는 여러분들이 B라는 프레임에서의 XYZ, 즉 $X_B$, $Y_B$, $Z_B$를 A라는 프레임에서, 표현하게 되면, [1,0,0], [0,0,1], [0,-1,0]이렇게 3 by 3 로테이션 매트릭스로 표현 가능하고 떨어진 거리는 [0,3,1]의 거리만큼 떨어져 있음을 알 수 있기 때문에
이와 같이, Homogeneous Transformation Matrix로 정의할 수 있고 두개를 곱했을 때, 바로 [0,2,2]로 앞서서 말씀드렸던 것처럼 뭔가 2개의 조합이 한가지로 이루어졌는데, 바로 이렇게 곱해버리니까, [0,2,2] 물론 밑에 1이라는 더미 텀이 있지만 이 더미 텀을 빼버리면
손쉽게, [0,1,1]이라는 B프레임에서의 점을 [0,2,2]라는 A프레임의 점으로 A프레임으로 충분히 쉽게 Homogeneous Transformation을 통해서 표현할 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (17).jpg){% endraw %}|

그렇다면, Homogeneous Transformation을 앞에서 살펴본 것처럼, 이렇게 2가지의 곱하기와 더하기로 이루어진 연산을 하나의 곱하기로 바꿔서 표현할 수 있다는 장점이 있다고 말씀드렸는데
그러한 장점만이 있는 게 아니라 좀 더 살펴보게 되면, 즉 한번의 Transformation 한번의 변환만을 할 경우에는 그다지 큰 장점이 없을 수도 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (18).jpg){% endraw %}|

그렇지만 위의 식처럼 C에서부터 B로 오고 B에서부터 A로가는 즉, C프레임에 있는 한 점을, B프레임으로 옮기고, 다시 A프레임으로 옮겨오는,이러한 2가지의 수식을 가지고 설명하는 것을 한번 진행해보도록 하겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (19).jpg){% endraw %}|

이 2개의 연산을 연속적으로 진행하게 되면, 즉 어떤 P라는 점을 A라는 프레임에서 설명하기 위해서 우리는 바로 이 A라는 프레임, B라는 프레임, C라는 프레임을 하나하나 거쳐서 이와 같은 조금은 복잡해보이는 수식으로 표현을 해야 합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (20).jpg){% endraw %}|

그렇지만 이 수식을 Homogeneous Transformation으로 표현한다면 C라는 프레임의 P는 바로 Homogeneous Transformation C에서부터 B까지 온 것을 곱해주고 그 곱한 것을 다시 B에서 A까지 가져오는 Homogeneous Transformation의 곱으로 곱해주면 바로 A라는 프레임으로 넘어오게 되죠.
앞서서 본 위의 이 수식 즉, 그냥 어떤 Rotation Matrix와 Origin의 어떤 거리 관계식 이런 것들로 설명한 식보다 훨씬 간단해진다는 것을 알 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (21).jpg){% endraw %}|

수식적으로는 동일한 효과를 얻으면서 생각은 훨씬 더 쉽게할 수 있습니다. 바로 이 Homogeneous Transformation 하나만으로 얼마든지 한번이건 두번이건 세번이건, 연속적으로 진행될때마다 각각을 곱해주기만 하면 바로 이 복잡한 연산이 단순하게 바뀔 수 있다는 장점도 가지고 있습니다.

## Inverse Transformation

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (22).jpg){% endraw %}|

일반적으로 Rotation Matrix같은 경우에는 앞서서, SO(3)에 포함되어 있기 때문에 자기 자신의 역행렬은 Transpose하고 일치한다,라고 설명한 바 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (23).jpg){% endraw %}|

그렇지만 Homogeneous Transformation같은 경우에는 확장을 했기 때문에 Homogeneous Transformation의 Inverse는 Homogeneous Transformation를 Transpose한 것과 완전히 같지는 않습니다.
특별히 그런 부분을 주의하기 위해서, Homogeneous Transformation의 Inverse를 다음과 같이 정의합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (24).jpg){% endraw %}|

즉, 앞서서 로테이션 매트릭스 자체는, 트랜스포즈 자체가 역행렬을 의미하기 때문에, 로테이션의 자리에는 바로 로테이션 매트릭스의 트랜스포즈 형태로 배치할 수 있고 원래 이 위치에는 B에서부터 A 즉, A에 대해서 B의 origin이 어떻게 표현되는지를 설명해야 하는데 역행렬이니까, 반대로 B라는 프레임에 대해서 A Origin의 위치를 써 넣어줘야 하는 것입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (24).jpg){% endraw %}|

그럼 어떻게 해야 하느냐, 바로 Inverse Transformation을 하게 된다면 즉 Rotation을 즉, B라는 프레임에 대해서 A라는 프레임으로 가져가게 된다면 Transpose한다면 역행렬이 된다고 했습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (25).jpg){% endraw %}|

그 역행렬에다가 B라는 origin을 A로 바꾸는 것을 곱해줌으로서 -를 곱해줌으로서 A origin을 B프레임에 대해서 설명할 수 있는 이러한 식이 완성되게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (26).jpg){% endraw %}|

그래서, 이 두 식을 여러분들이 Homogeneous Transformation Matrix, 즉 B에서부터 A까지 오는 Homogeneous Transformation의 Inverse는 이와 같이 정의되고 이 정의된 것을 A에서 B까지 오는 Homogeneous Transformation이라 말할 수도 있습니다. 그리고 그 2개를 같이 곱했을 때, 당연히 역행렬이기 때문에, Identity Matrix를 만족해야합니다.
수식으로 계산해보면 쉽게 Identity Matrix가 된다는 것을 확인할 수 있게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-5 (27).jpg){% endraw %}|

여기까지 살펴봄으로서, 여러분들은 Homogeneous Transformation이 어떻게 구성되고 어떤 장점을 갖고 있는지 이 Homogeneous Transformation의 Inverse는 어떻게 계산하는지를 살펴보았습니다





