---
title: "Robot Manipulator and Underwater Robot Application 4주차 4-1 Introduction"
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
last_modified_at: 2019-04-08
comments: true
mathjax: true
classes: wide
---

## Kinematics

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-1.jpg){% endraw %}|
|*우리는 주로 기구학에서 정기구학, 역기구학, 이 두 가지 topics을 다룰 예정 입니다.*|

### Foward Kinematics

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-1 (2).jpg){% endraw %}|

먼저 Forward Kinematics라고 하는 것은 만약에 로봇을 설계했다라고 하면, 설계된 로봇의 각각의 Link에 대한 길이를 가지고 있을 것이고 그 각각의 Link들을 joint 즉, 모터를 활용한 joint를 통해서 두 개의 Link를 연결을 했을 것입니다.
그리고 그 각각의 조인트(joint)는 역시 앞서 설명 드렸던 것처럼, encoder라던지 위치를 측정할 수 있는 Sensor들을 바탕으로 각도를 측정할 수 있습니다.

이렇게 준비되었다면, 이러한 정보들을 바탕으로 로봇의 Link와 Joint에서 나오는 각도 정보를 바탕으로 각각의 각도들을 이용해서
마지막 끝점(end-effector)의 위치를 어떻게 찾아낼 수 있느냐. 하는 부분들을 ‘Forward Kinematics’라고 얘기를 하는 것입니다.

### Inverse Kinematics

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-1 (3).jpg){% endraw %}|

이와 반대로 ‘Inverse Kinematics’라고 하는 것은 끝점의 위치를 고려했을때, ‘로봇의 끝점의 위치를 이렇게 이동하겠다.’ ‘직선 방향으로 이동하겠다.’ 라고 하는 공간상에서의 위치 점들이 있을 것입니다.

이런 위치 점들에 가기 위해서는 각각의 관절들의 각도들을 어떻게 꺾어 줘야지만 이 위치로 갈 수 있는지라는 이 문제의 Solution을 찾아내는 방법을 역 기구학 또는 Inverse Kinematics라고 부릅니다.

## Basic Problems in Robotic Kinematics

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-1 (4).jpg){% endraw %}|

그렇다면 앞서 설명 드렸던 내용들을 그림으로 살펴보시면 이렇게 각각의 각도들 $\theta_1$, $\theta_2$, $\theta_3$, $\theta_4$, $\theta_n$까지 이러한 $\theta$에 대한 정보들을 각각의 로봇이 가지고 있는 joint에서의 각도, joint 각도를 순서대로 아래쪽에서부터 연결을 해서 그것들을 표현한 것을 각도 $\theta$에 대한 벡터라고 표현할 수 있습니다.

그리고 끝점에서의 위치는 $x$, $y$, $z$만이 될 수도 있을 거고 또는 $x$, $y$ ,$z$와 각각의 Roll pitch yaw 각도, 아니면 특정한 오일러각도 아니면 여러분들이 앞서 배운 각도 표현법에 따른 그러한 각도를 포함하는 위치 백터인 $X$에 대해 이렇게 표현할 수가 있습니다.

그래서 정리하자면, 이런 $\theta$가 주어졌을 때, $X$를 찾는 문제를 ‘정 기구학’ 또는 ‘Forward kinematics’라고 얘기합니다.

그리고 $X$가 주어졌을 때, $\theta$를 찾는 것을 ‘Inverse Kinematics’라고 얘기를 하고 “역 기구학을 찾는다.”라고 표현을 하고 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-1 (5).jpg){% endraw %}|
|*그리고 그 역인 $X$가 주어 졌을때, $\theta$를 구하는 문제를 또다시 위치 수준과 속도 수준으로 나눠서 생각을 해 보실 수 있습니다.*|

위치 수준에서는 우리가 앞서서 구했던 ‘homogeneous transformation’을 통해서 어떻게 이 $\theta$가 주어졌을 때, 어떻게 $X$가 나오게 되는지에 대한 수식을 살펴볼 텐데요. 이렇게 나오는 수식은 기본적으로 ‘Non-Linear 하다.’라는 성질을 가지고 있습니다.
여러분들이 ‘Non-Linear하다.’라고 하는 개념에 대해 생각을 해보게 된다면 어떠한 $\theta$값 1을 줬을 때, 나오는 $X_1$와 $\theta$값 2를 줬을 때 나오는 $X_2$ 이 두 개의 값이 더해서 새로운 앞에서 말씀드렸던 $X_1$과 $X_2$가 $\theta_1+\theta_2$에 들어갔을 때, 나오는 값과는 다르다는 그러한 개념이 보통 ‘비선형’ ‘Non-Linear하다.’라고 얘기를 합니다.
이러한, Non-Linear 문제는 생각보다 풀기 쉽지 않고, ‘각각의 Solution들을 따로따로 찾아내야한다’라는 문제점들을 가지고 있습니다.

그에 반해서 속도 수준에서는 추후에 ‘Jacobian’이라는 것에 대해서 공부를 하게 될 텐데 이 ‘Jacobian’에 의해서 속도 즉, 관절을 움직이는 속도와 그리고 그 관절 속도에 의해서 나타나는 끝점에 속도는 ‘Jacobian’이라고 하는 그런 matrix를 통해서 선형 관계식으로 만들어낼 수가 있습니다. 그래서 위치 관계식과 속도 관계식에서, 위치 관계식은 비선형이고 속도 관계식은 선형 이라는 그러한 장점을 가지고 있습니다. 그렇지만 속도 관계식을 이용을 했을 때는 원하는 것은 각각의 위치 점을 찾아가는 문제이기 때문에 역시 또 속도 관계식만 가지고 쓰기에는 좀 한계가 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-1 (6).jpg){% endraw %}|

이어서 ‘Degree of freedom’에 대한 설명을 잠깐 드리겠습니다.

‘Degree of freedom’이라고 하는 것은 어떠한 움직임을 만들어 내기 위해서 필요한 변수들의 집합이라고 보면 되겠습니다.
자유도 라고 불리는 것에 대해서 여러분들은 두 가지 측면에서 접근해 볼 필요가 있습니다.
자유도 라고 하는 것은 물체를 완벽하게 어떻게 위치하고 있고 자세를 취하고 있는지를 기술할 수 있는
그러기 위해서 필요한 $x$, $y$, $z$와 같은 위치, 그리고 Roll, pitch, yaw와 같은 각도, 이런 정보들의 집합을 자유도 라고 합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-1 (7).jpg){% endraw %}|

만약에 공간상에 떠다니는 비행기를 생각해 본다면 비행기의 기준점으로 부터의 위치 즉, $x$, $y$, $z$라는 공간상에서의 세 개의 좌표로 표현되는 점이 있을 거고요. 그리고 이 비행기가 취하는 자세에 따라서 우리는 정확하게 이 비행기를 설명하기 위해서는 여섯 개의 좌표가 필요하게 됩니다. 그렇기 때문에 우리는 이 비행기를 ‘6 자유도 운동을 하는 물체다.’라고 설명을 할 수가 있습니다. 그리고 평면상에서 움직이는 자동차의 경우에는 평면상에서의 자동차는 $x$, $y$, 하고 자동차의 방향, 이 세 가지를 가지고 자동차를 정확하게 ‘어디에 있다.’ 라고 기술할 수 있기 때문에 ‘자동차는 3 자유도를 가지고 있다.’라고 할 수 있겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-1 (8).jpg){% endraw %}|

이렇게 공간상에서의 자유도라고 하는 것은 공간상에 자유도는 이렇게 위치에 대한 Translation에 대한 자유도를 보통 3차원이면 3개, 2차원이면 2개를 가지게 됩니다. 그리고 자세에 대한 자유도는 2차원이면 위에 보이는 식처럼 이 Rotation에 대한 자유도 2 dimensions이면, d 에다가 2를 대입해서 계산을 해 보면 1이라는 자유도 즉, 방향각에 대한 자유도만 나오게 됩니다. 3차원이 되면 3개의 자유도 ‘Roll pitch yaw’와 같은 ‘3개의 오일러 각’에 의한 자유도를 나타내게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-1 (9).jpg){% endraw %}|






