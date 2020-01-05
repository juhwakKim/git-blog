---
title: "Robot Manipulator and Underwater Robot Application 6주차 6-1 Jacobian matrix"
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
last_modified_at: 2019-04-26
comments: true
mathjax: true
classes: wide
---

## Jacobian matrix

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1.jpg){% endraw %}|

그렇다면 먼저 Jacobian matrix를 유도하기 앞서서 먼저 Jacobian matrix를 유도하기 위한 속도에 대한 Rotational, 회전하는 속도에 대한 관계식들을 먼저 정의해볼 필요가 있습니다.

첫번째, object가 rotational velocity, 즉 회전속도에 의해서 이동하고 있었을 때 그랬을 때 어떠한 각도로 표현되는 것을 이 각도의 속도, 즉 각도의 변화량으로써 어떻게 표현할 수 있는지는 보통 두 가지 정도로 요약해서 나타낼 수가 있습니다.
첫번째 앞서서, 기구학 부분에 있어서 Euler angle 하고 roll/pitch/yaw라는 각도를 이용을 해서 각도표현을 하는 법을 배웠습니다.
Euler angle하고 roll/pitch/yaw 입장에서 만약에 이런 Euler angle하고 roll/pitch/yaw 를 $\phi$라고 정의를 했을 때, 어떠한 두 좌표계사이의 관계식이 됩니다.
두 좌표사이에 roll/pitch/yaw 또는 Euler angle로서 transformation이 가능할텐데요.
이랬을때 roll/pitch/yaw 가 각각 속도로써 나타내게 될 때 roll/pitch/yaw 를 아니면 Euler angle을 미분하게 됐을 때, 즉, 시간에 대해서 미분했을 때, 그 미분한 항을 각각 각도에 대한 속도로써 표현이 가능 할 겁니다.

### Rotational Velocity of a Object

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(2).jpg){% endraw %}|

그랬을 때 이렇게 표현을 하게 되면 roll/pitch/yaw 에 대한 아니면 Euler angle에 대한 속도를 적분을 하게됩니다.
적분을 하게되면, 그 적분한 값이 가지는 의미는 결국에는 정의했던 roll/pitch/yaw 또는 Euler angle의 파라미터 앵글로써 표현이 될 수 있겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(3).jpg){% endraw %}|

그런데 문제는 이렇게 roll/pitch/yaw 라던지 Euler angle 같은 것들을 속도관계식을 가지고 미분하고 적분해서 얻어지는 관계식을 설명하는 것은 굉장히 쉽습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(4).jpg){% endraw %}|

문제는 이러한 roll/pitch/yaw 라고 하는 것들 아니면 Euler angle이라고 하는 각도들의 변화량이 직접적으로 이 각도로써 표현이 될 수 있는 부분은 아닙니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(4.5).jpg){% endraw %}|

어떤 의미냐 하면, 비행기를 상상해보면, 앞서서 기구학을 설명을 할 때, 기구학에서의 각도표현을 설명할 때 비행기를 가지고 roll/pitch/yaw 라던지 Euler angle을 설명드린적이 있었습니다.
비행기를 생각했을 때 이 비행기가 가지고 있는 예를 들어서 X방향에 대한 roll 또는 pitch 그다음에 yaw를 봤을 때, 만약에 yaw가 단독으로 나타나거나 아니면 pitch가 단독으로 나타날때는 큰 문제가 없지만,\
yaw하고 pitch가 동시에 나타나는 운동, 동시에 나타나는 움직임이 있었을 때, 시시각각 계속해서 이 속도가 변할 때 각각에 대한 값들을 정확하게 표현하는 것은 이러한 Euler angle, roll/pitch/yaw 각도들을 rotation matrix로부터 뽑아낸 각도이기 때문에 1대1 mapping이 되지 않습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(5).jpg){% endraw %}|

따라서 사실상 어떤 각도를 표현하고 그 각도에 대한 rate, 즉 각속도를 표현할 때는 그 표현법이 조금은 달라져야 될텐데요
일단은 가장 기본적인 물리 법칙에서는 $\omega$로써 이 각도에 대한 변화량 즉, 속도변화를 보통 표현합니다.
그래서 원하는 roll/pitch/yaw, Euler angle 같은 변화량은(속도는) 이러한 $\omega$의 값으로, 일반적인 좌표계를 설명하는 오메가의 값을 이용해 표현을 해야 할 필요가 있습니다.
그래서 뽑아내는 roll/pitch/yaw 각도 또는 Euler angle 값에 따라서 각각 뽑아내는 방법이 다르기 때문에
역시 그 둘 사이에 매칭을 가져가게 되는 표현법은 또 역시 달라지게 될 것 입니다.
옆에 보이는 수식은 대표적으로 ZYZ앵글로써 뽑은 Euler angle값을, 그 Euler angle값과 $\omega$의 어떤 관계식을 뽑아낸 수식이 되겠습니다.
이 수식이 어떻게 이렇게 유도되었는지에 대해서는 차차 진행을 하면서 설명을 드리기로 하겠습니다.
이런식으로 수식을 유도를 하게되면 우리는 roll/pitch/yaw에 대한 각각의 변화량, 또는 Euler angle에 대한 변화량을 오메가로써 표현하는 이러한 방법을 얻게 되는 것 입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(6).jpg){% endraw %}|

이것들은 아무래도 roll/pitch/yaw 라는 값들을 직관적으로 알 수가 있습니다.
그 알 수 있는 값들을 속도로써 기술함으로써 우리에게 전달되면 physical meaning, 물리적인 의미가 명확합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(7).jpg){% endraw %}|

이와 반대로 사실상 각도표현법이라고 하는 것들은 앞서서 말씀드렸지만 rotation matrix로 가지고 온 것들입니다.
각도표현법에 있어서 rotation matrix를 설명 드릴 때 이러한 rotation matrix 같은 경우에는 어떤 임의의 축, 임의의 축에 대해서 회전하는 Euler's theorem으로 표현이 가능하다고 얘기했습니다.
그러면 두 개의 좌표계가 있었고, 그 두 개의 좌표계 사이의 각도가 Euler angle 또는 다른 방법이 아닌 그냥 그 자체로써 이 rotation matrix가 회전하는 것으로 표현할 수 있는 방법은 없을까라는 그러한 표현법을 생각해 볼 수가 있겠습니다.
앞서서 말씀드렸던 Euler axis라고 불리는 특정한 그 각도, 그 각도에 대해서 어떤 일정한 각도만큼 돌리면 두 개의 좌표계를 일치시킬 수 있다고 앞서서 말씀드린 적이 있었습니다.
그것들을 이용해서 임의의 축을 찾을 수 있고, 그 축에 대해서 어떠한 rate을 찾을 수 있다면, 회전하는 rate을 찾을 수 있다면, 두 개의 좌표계를 어떤식으로 회전이 일어나는지에 대한 설명이 가능해지는 것입니다.
이렇게 두번째 방법으로 $\omega$라는 값을 이용해서 어떤 축과 그 축에 대해서 회전하는 값, 회전하는 양에 대해서 표현하는 방법도 역시 있겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(8).jpg){% endraw %}|

그래서 이 두번째 방법, 이 두번째 방법을 두 좌표계 상에서의 수학적인 표현법으로서 명확하게 표현하는 것은 매우 쉽습니다.
또 하나 예를 들어서 두 좌표계사이의 rotation matrix가 바뀌어가는 그 rate을 계측을 해서 써먹어야 된다라는 측면에서 봤을 때

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(9).jpg){% endraw %}|

계측을 하기 위해서는 일반적으로는 만약에 비행기라고 하면 비행기에 장착되어 있는 IMU센서센서라고 불리는 이러한 자체의 gyroscope하고 accelerometer 같은 것들을 활용해서
이 자체의 회전 각속도를 측정하게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(10).jpg){% endraw %}|

이러한 회전 각속도를 측정할 때는 각각은 겉에서 보기에는 다른 좌표계에서 보기에는 정확하게 의미가 뭔지를 모르겠지만
이 $\omega$라는 값 같은 것들은 결국에는 어떠한 비행기라던지 움직이는 물체가 이렇게 자세를 취하고 있을 때, 이 자세, 취한 자세에서 이 자세를 똑바로 놨다라고 봤을 때
그 자세에서 이루어지는 각각의 축에 대한 속도를 gyroscope 같은 것들로 얻게되는 것입니다.
그래서 이러한 Angular velocity vector같은 경우들은 센서로부터 얻고 그리고 두 좌표계를 명확하게 설명할 수 있다는 큰 장점이 있는 반면에
문제는 이러한 $\omega$를 직접적으로 접근했을 때, $\omega$를 직접적으로 접근했을 때 얻게 되는 건 무엇이지? 라고 했을 때 명확한 물리적 의미 같은 것들은 파악하기가 어렵다는 단점을 가지고 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(11).jpg){% endraw %}|

그래서 첫번째 방법은 physical 의미가 명확하고 yaw방향으로 얼마나 변했는지, roll방향으로 얼마나 변했는지를 정확하게 설명하는 속도표현법이었습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(12).jpg){% endraw %}|

두번째 방법은 수학적으로 딱맞게 떨어지고 수학적으로 유도가 편한 그런 장점, 그리고 실질적인 센서를 활용해서 속도를 측정하는 그런 측면에서 유리한 그런 성질을 가지고 있다라고 할 수 있겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(13).jpg){% endraw %}|

이렇게 속도를 표현하는 방법에 대해서 살펴보았습니다.
이러한 속도표현법을 바탕으로 이제는 Jacobian matrix라는 것을 먼저 정의를 하고 다시또 이어서 속도기구학에 대한 이야기를 해보도록 하겠습니다. 
만약에 옆에 보이는 식처럼 $\eta$라고 하는 식이 함수$f$로 주어져있고 그 function들은, 함수들은 $\xi_1$ 부터 $\xi_k$까지의 변수들의 함수라고 생각을 해 보면,
이랬을 때 $\eta$ 같은 경우에는 $\eta_1$부터 $\eta_l$까지 l개의 파라미터를 가지고 있고, $\xi$ 같은 경우에는 $\xi_1$ 부터 $\xi_k$까지 $k$개의 파라미터를 가지고 있다고 한번 생각해보시죠.
그랬을 때 만약에 $\eta$하고 $\xi$ 사이에 어떠한 속도, 즉 미분관계식을 가지는지를 한번 살펴보도록 하겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(14).jpg){% endraw %}|

$\dot \eta$을 미분을 하고 $\dot \xi$에 미분된 식과 비교하기 위해서 $J$라고 하는 이러한 매트릭스를 통해서 둘 사이를 표현할 수 있다면,
$\dot \eta$과 $J \dot \eta$이라고 하는 옆에 보이는 이러한 식처럼 선형관계식을 찾아낼 수 있을 것입니다.
이랬을 때 이 $J$라고 불리는 매트릭스가 어떻게하면 정의가 될 수 있는지를 앞서 수학적 기초에서 설명을 드렸던 체인룰에 의해서 설명하는 방법이 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(15).jpg){% endraw %}|

벡터를 벡터로 미분하는 관계식에 대해서, 아랫변에는 벡터의 Transpose를 넣어주고 윗쪽 분자에는 벡터를 아래로 긴 벡터 형태로 넣어주고
두 관계식을 Chain rule을 쓰기위한 매트릭스 형태로 이렇게 만들어 주게 되면, $J$를 이와 같이 정의한다면 앞서서 말씀드렸던 $\dot \eta$ = $J \dot \xi$ 이라고 하는 선형관계식이 유도가 되게 되는 것입니다.
그리고 그 중간에 $J$라고 하는 것은 각각 두 벡터들 사이에서의 미분관계식을 표현하고 있습니다. 그래서 이 미분관계식을 Jacobian matrix라고 이야기 합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(16).jpg){% endraw %}|

이 Jacobian matrix라고 하는 것은 로봇쪽에서만 쓰이는 것은 아니고 일반적으로 어떤 수식들이 두개의 좌표계, 두개의 어떤 공간이 있을 때 두개의 공간의 어떤 관계식을 설명할 때 그 관계식을 미분의 형태로 설명을 해보자 라고 할때는
그 중간의 매개체가 전부 다 Jacobian matrix가 되는 것 입니다. 따라서 이 Jacobian matrix는 여러분들이 다른 분야에서도 널리 들을 수 있는 그런 내용입니다.
로봇쪽에서도 역시 마찬가지로 이러한 Jacobian matrix를 또 살펴보시게 될텐데, 각각에서 쓰이는 의미들은 조금씩 다를 수 있지만 내용, 그 자체, 이 Jacobian matrix 그 자체가 포함하고 있는 어떤 의미들은 동일하다라는 것을 여러분들은 기억해두시면 되겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(17).jpg){% endraw %}|

그렇다면 우리는 이러한 Jacobian matrix를 가지고
앞서서 말씀드린 것 처럼 end-effector velocity, 끝점의 운동을 바로 joint velocity, 이 둘 사이의 관계식을 속도관계식으로써 한번 표현해보실 수 있을텐데요.
앞서서 보여드렸던 표를, 앞서서 보여드렸던 $\dot \eta$, $\dot \xi$을 Jacobian에 연결한 것과 마찬가지로,

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(18).jpg){% endraw %}|

앞서서 살펴봤었던 기구학, 즉 $r=f(\theta)$, 여기서 $r$은 끝점, 작업공간에서의 움직임이 되겠습니다.
$\theta$는 관절공간에서 움직임으로 기술 했었습니다. 이랬을 때 $r$ 하고 $f(\theta)$ 많이 보신 느낌이 들죠. $r$은 예를 들면 $r_1$ 부터 해서 $r_n$까지, 만약에 3차원 공간에서의 6개의 공간에서의 좌표를 표현한다면 6개가 되겠고 $\theta$는 거기에 따라서 만약에 6자유도 manipulator면 6개,7자유도 manipulator면 7개 이런 형태의 dimension을 가지게 되겠습니다.
이것들을 미분을 하게되면, $r$이라고 하는 것은 결국에는 위치하고 Euler angle 또는 parameterized된 각도들이 될텐데
그 각도들을 가지고 각각 미분을 취하게 되면, 옆에 보이는 식처럼 $\dot r = J_r(\theta) \dot \theta$. 즉, 이 $r$을 가지고 바로 $\theta$를 표현한 Jacobian matrix $J_r$을 유도할 수 있겠고
이 때 이 $J_r$은 $\partial r \above 1pt \partial \theta^T$ 즉, $r$을 $\theta^T$의 벡터로써 미분한 형태가 Jacobian의 형태가 되겠죠. 자 이게 method1의 표현법이었습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(19).jpg){% endraw %}|

method 2에서 아까 말씀드렸던 $\omega$와 그다음에 $\omega$와 각도의 그 관계식, 각각의 조인트 각도의 관계식으로서 표현을 한번 해 볼텐데 속도라고 하는 $v$라고 하는 것을 $j_v(\theta) \dot \theta$이라고 $J_v$를 찾고 싶습니다.
즉 $v$하고 $\dot \theta$. 여기서 $v$는 generalized 되어있는 velocity, 즉 위치에 대한 $\dot P$과 그 다음에 아까 각도표현법을 $\omega$로 한번 표현했습니다.
두 번째 방법으로는, 그래서 그 $\omega$하고 $\dot P$으로써 기술되어 있는 벡터 $v$는 결과적으로 $\dot P$ 같은 경우에는 그대로 연결이 되고 그 속도에 대한 velocity는 그대로 연결이 되는데
$\omega$ 같은 경우는 이 $\omega$는 직접적으로 계측은 되지만 의미가 없다라고 해서 중간에 어떠한 $Q$라던지 이런 매트릭스 형태로 $\dot \Phi$과 함께 정의를 했었습니다.
그래서 $Q \dot \Phi$ 이라고 가정을 한다면 $\omega$는 $Q \dot \Phi$ 이 될거고, 그것들을 쭉 풀어서 앞에있는 각각 $\dot P$과 $\dot \Phi$의 형태를 그대로 유지하게 하기위해서 새로운 매트릭스를 만들어주면
$\dot P$은 그대로 연결이 되니까, 윗쪽 3by3 매트릭스는 Identity 매트릭스, 그리고 $\dot P$은 $\dot \Phi$과 그다음에 역시 마찬가지로 $\dot \omega$도 $omega$나 이런 함수들도 $\dot P$하고 관련이 없기 때문에
대각텀들은 3by3 0매트릭스가 배치가 되고 그 다음에 대각선 아랫쪽은 $Q_r$로 이렇게 매트릭스 옆에 보이시는 이러한 형태로 새로운 식을 만들 수 있겠고
이렇게 만들어지면 조금전에 method 1에서 정리했었던 $J \dot \theta$ 형태로 $\dot P$과 $\dot \Phi$에 의한 식을 유도할 수 있게 되는 것 입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(20).jpg){% endraw %}|

그렇게해서 최종적으로는 $J_v = T_rJ_r$형태로 이렇게 용어들이나 기호들은 조금씩 바뀔 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(21).jpg){% endraw %}|

지금 전달드리고 싶은 내용들은 정의한 parameterized 된 velocity, 즉 roll/pitch/yaw 라던지 Euler angle이라던지
이런 값들로써 얻어진것들의 속도관계식과 조인트 공간, 관절공간에서의 속도관계식을 연결하는 Jacobian과, $\omega$,
공간상에서의 좌표계의 움직임을 직접적으로 표현할 수 있는 속도와 $\omega$로 표현되어있는 그 공간과 관절공간의 관계식, 이 두가지를 다 우리는 Jacobian이라는 것으로써 얘기할 수 있는데,
두 가지 의미 차이는 조금 있다라는 것. 이것을 조금 기억해두시는게 좋을 것 같습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(22).jpg){% endraw %}|

그러면 이러한 Jacobian을 3링크 manipulator에 대해서 먼저 한번 연습을 진행 해 보도록 하겠습니다.
이러한 planar, 이 평면상에서 구동되고 있는 3링크 manipulator를 그림과 같이 가정을 해 보시죠.
이렇게 $\theta_1$ $\theta_2$ $\theta_3$로 이뤄진 이 3링크 manipulator에 대해서 연습을 진행해보도록 하겠습니다.
각각의 $x y \phi$ 그 끝점에서의 위치값을 $x y$ 그다음에 $\phi$라고 표현을 한다면
아마 앞에서 2링크 3링크 manipulator의 예를 들면서 식들을 유도한 기억이 있을텐데요.
이렇게 $x y \phi$ 를 각각 미분을 하게 되면 $\dot x \dot y \dot \phi$ 이렇게 주어지고 식들은 옆에 보이는 식처럼 각각의 $x y \phi$를 미분한 형태로써 나타낼수가 있을 것 입니다.
이렇게 미분한 형태를 나타난 식들을 바탕으로 여기에서 보시면 앞에는 분명히 $\dot x \dot y \dot \phi$ 이라고 하는것은 정의했던 작업공간상에서의 속도가 되겠고 그 각각의 식들을 $\dot \theta$, $\dot \theta_1 \dot \theta_2 \dot \theta_3$ 이렇게 세개의 관절공간에서의 속도하고 매칭을 시켜보았습니다. 

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA6-1_(23).jpg){% endraw %}|

이렇게 매칭을 시켜놓고 이것들을 다음과 같이 정리를 해 보면 $J_r$ 이라고 얘기를 하고
이 $J_r$에 각각의 텀들을 이렇게 표현, 그 각각의 인자들을 전부다 따서 이렇게 매트릭스 형태로 표현을 한다면 최종적으로 앞서서 보여드렸던 것 처럼 세타닷을 이용해서 $J$라는 것을 곱해줌으로써,
$J \dot \theta$을 곱해줌으로써 원하는 $\dot x \dot y \dot \phi$을 정의하는 식, 즉, Jacobian matrix를 정의할 수 있게 되는 것 입니다.

