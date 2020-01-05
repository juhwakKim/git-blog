---
title: "Robot Manipulator and Underwater Robot Application 3주차 3-3 Euler Angles(1)"
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
last_modified_at: 2019-04-05
comments: true
mathjax: true
classes: wide
---

## Euler Angles

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3.jpg){% endraw %}|

어떤 Rotation을 한 프레임에서 다른 프레임으로 바꿀 때 3개의 Simple Rotation 앞서서 3개의 Rotation Matrix에서는 3개의 파라미터를 가지고 표현할 수 있습니다.

이렇게 이 3개의 파라미터를 3개의 Simple Rotation이라는 개념을 통해서 어떠한 프레임에서 다른 프레임으로 항상 바꿀 수 있다 라고 하는 그러한 방법이 바로 Euler Angles입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (2).jpg){% endraw %}|

이 Euler Angles은 하나의 어떤 Angle을 어떤 특별한 축에 대해서 하나의 Angle을 통해서 Rotation이 이루어지고 그러한 것들을 조합함으로서 원하는 Rotation Matrix를 만들어낼 수 있다 라고 하는 것이 바로 Euler Angles입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (3).jpg){% endraw %}|

이런 축이 아닌 즉 $x$방향 $y$방향, $z$방향, 또는 $x$방향, $z$방향, $x$방향, 즉 이렇게 3개의 Rotation을 만들어내는 어떠한 조합 이러한 3개의 회전이 만들어지는 조합은 총 12개를 만들어낼 수가 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (4).jpg){% endraw %}|

12개의 이 조합 중에서 가장 널리 쓰이는 조합은, ZYZ라고 하는 조합입니다.

마지막에 로봇 축 같은 것들이 회전하고 이동하고 마지막에 그리퍼까지 만들어지는 과정이 $z$축에 대한 회전, $y$축에 대한 회전,다시 $z$축에 대한 회전 으로 로봇의 구조와 회전이 이루어지기 때문에 이러한 회전으로서 마지막 말단 장치의 좌표계를 설명할 수가 있습니다.

ZYZ라는 이러한 방법을 통해서 이 로봇의 회전을 표현하는 데에 유리하기 때문에 ZYZ라는 방법이 널리 쓰입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (5).jpg){% endraw %}|

첫번째로 $z$축에 대해서 회전을 한번 구현하고 그 다음에 돌아간 회전축에 대해서 다시 한번 $y$축에 대한 회전을 구현하고 다시 돌아간 축에 대해서 마지막으로 $z$축에 대해서 회전을 하게 되면, 즉 $z$축, $y$축, $z$축을 한번씩 돌아가면서 반복함으로서 어떠한 회전을 정확하게 표현하는 방법 입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (6).jpg){% endraw %}|

이렇게 표현하는 방법들을, 총 12가지의 시스템, 즉 트웰브 시스템이라고 말하는데, 표현 방법에 따라서, 이런저런 조합에 따라, 각각 표현하는 방법들이 달라질 수 있다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (7).jpg){% endraw %}|

A라는 프레임과 B라는 프레임이 이렇게 존재하고 있을 때, 이 A라는 프레임과 B라는 프레임을 회전하는 규칙을 나는 Z축을 한번 돌리고, Y축을 한번 돌리고, Z축을 다시 한번 돌려서, 이렇게 만들거야, 라는 규칙을 정했다면 나는 ZYZ라는 방법으로 각각 10도, 20도, 30도 만큼 돌렸을 때 이렇게 나왔다, 라는 것을 다른 사람에게 설명한다면 다른 사람들도 역시 마찬가지로 이 사람이 Z축으로 10도, Y축으로 20도, Z축으로 30도 돌렸을 때 되는구나, 하고 납득하고 똑같이 하면 된다는 규칙 설명에 있어서, 좋게 작용할 것이기 때문에 이러한 규칙에 의해서 이렇게 회전을 정의하게 됩니다.

## Euler Angles의 장단점

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (8).jpg){% endraw %}|

장점은 어떤 로봇을 만들 때, 대부분 아까 설명했던 것처럼 로봇의 말단 장치에서 이 말단 장치가 마지막에 구성되는 방식이
$z$축과 $y$축과 $z$축의 어떤 순서로 마지막 손목 조인트들이 구성됩니다.

이러한 방식처럼 또 다른 방법으로 손목을 만들 수도 있는데 이렇게 만들었을 때, 이러한 방법들대로 회전이 이루어지기 때문에, 마지막 말단 장치에서의 어떤 회전의 방향을 정확하게 표현할 수 있다, 라는 장점을 가지고 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (9).jpg){% endraw %}|

단점은 2가지 솔루션이 존재할 수 있다는 것입니다. 즉 회전을 어떤 방식으로 표현하느냐에 따라서, 이 표현하는 방법이 동일한 표현, 동일한 어떤 각도 표현법이지만 여러가지로 표현될 수 있지만 그에 대해 명확한 정의를 내리지 않는 경우에는, 혼동을 불러일으킬 수 있다는 점이 단점으로 작용합니다.

## ZYZ의 종류

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (10).jpg){% endraw %}|

그렇다면, 금방 말씀드렸던 이런 혼동이 있을 수 있다 라는 것들에 대해서 살펴보게 되면 ZYX relative rotation, XYZ absolute rotation이라고 하는, 두 가지의 Euler Angles이 존재합니다

다른 말로 하자면 Roll, Pitch, Yaw라고 정의되어 있는, Roll, Pitch, Yaw을 바로 ZYX relative rotation, 또는 XYZ  absolute rotation이라고 정의할 수가 있는데 ZYX relative rotation과, XYZ absolute rotation은 결과를 먼저 말씀드리자면 동일한 Rotation을 의미합니다.

### ZYX relative rotation

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (11).jpg){% endraw %}|

ZYX relative rotation이라고 하는 것은 먼저 $z_0$에 대해서 $\alpha$만큼 회전하고, $y_1$축에 대해서 $\beta$만큼 회전하고 다시 $x_2$축에 대해서 $\gamma$만큼 회전하는 것들이 차례대로 이루어져 있는 것들을 말합니다. 

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (12).jpg){% endraw %}|

이 relative rotation의 의미는 이 Matrix 자체가 앞에서부터 $\alpha$, $\beta$, $\gamma$의 순으로 위의 수식대로 배치되어 있지만 사실상 앞에서 말씀드린 것처럼 어떤 좌표상에서 표현되는 점 $p$를 1번 좌표계에서 0번 좌표계로 이동을 해올 때 맨 오른쪽에 먼저 곱해주게 되면 오른쪽에 곱해졌을 때 먼저 반영되는 것은 먼저 $x$축에 대해서 $\gamma$만큼 회전하고 그렇게 이루어진 다음에 다시 $y$축에 대해서 $\beta$만큼 회전이 이루어지고 다시 회전이 다 이루어진 그 좌표계를 다시 $z$축에 대해서 $\alpha$만큼 회전하는 즉 차례대로, 거꾸로, 하나씩 오게 되기 때문에 그 순서가 ZYX, 즉 표현법과 매트릭스 자체는 $z$축에 대한 회전, $y$축에 대한 회전, $x$축에 대한 회전이라고 할 수 있습니다.

그렇지만 실제로는 $x_2$, $y_1$, $z_0$에 대해서 순차적으로 회전이 이루어지는 그런 방식이기 때문에, ZYX relative rotation이라고 표현하게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (13).jpg){% endraw %}|

그래서 위에 있는 그림처럼, 실제로는 여러분들이 회전에 대한 이해를 거꾸로 $x_2$와 $x_3$가 일치되어 있는 마지막 그림에서부터 먼저 $x_2$축에 대해서 회전, $y_1$축에 대한 회전, $z_0$축에 대한 회전을 통해서 마지막 전이, 즉 1프레임에 있었던 어떤 포지션이 다른 프레임으로 회전이 이루어지는 과정의 일환이라고 보면 되겠습니다.

### XYZ absolute rotation

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (14).jpg){% endraw %}|

반대로, XYZ absolute rotation이라고 하는 것은 먼저 쓰는 방식으로 보면,
$x$축에 대한 회전, $y$축에 대한 회전, $z$축에 대한 회전 즉, 이 순서로 보면 위에 있는 이 매트릭스처럼 처음에 놓여 있는 순서는 분명히 $z$축에 대한 $\alpha$만큼 회전 그 다음에 그 $y$축에 대한 $\beta$만큼의 회전 그리고 $x$축에 대한 $\gamma$만큼의 회전이 있는데 XYZ, 즉 $x$축에 대한 회전이 먼저 일어나고 다음에 $y$축에 대한 회전이 일어나고 $z$축에 대한 회전이 일어난다는 의미에서 XYZ로 표현하는 방식은 absolute 방식입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (15).jpg){% endraw %}|

왜 absolute 방식인지에 대한 설명은 이 그림을 통해 살펴볼 수 있습니다.

즉, 회전이 이루어지는데 먼저 이 $x$축에 대한 회전을 수행한 다음, 다시 $x_0$, $y_0$, $z_0$에서의, $y_0$방향으로의 $y$축 회전을 이루고 그 다음에 역시 $x_0$, $y_0$, $z_0$에서 $z_0$ 방향으로 $z$축 회전을 수행하는 

즉, 고정되어 있는 첫번째 좌표계는 그대로 유지하면서 각각의 좌표계가 그 좌표계에 대한 회전으로 표현하는 방법을 XYZ absolute rotation이라고 말합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (16).jpg){% endraw %}|

ZYX relative rotation과 XYZ absolute rotation 2가지 방식은 동일한 회전을 의미 합니다.

이 두가지 동일한 회전은 어떤 측면에서 봤을 때는 이 회전이 이렇게 이루어졌는지, 다르게 이루어졌는지 정확히 설명하지 않으면 혼동이 일어날 수 있다.

즉 이렇게 2가지 표현방식으로 이루어질 수 있다는 단점을 가지고 있기 때문에 명확하게 어떤 식으로 회전을 한다는 것을 명확하게 설명하는 것이 필요합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (17).jpg){% endraw %}|

그렇다면, 이러한 회전이 이루어졌을 때, 앞서서 말한 것처럼, 우리는 총 9개의 파라미터들을 갖고 있고 9개의 equations 중에서 3개의 파라미터 즉 회전이 각각 ZYX 방향으로 얼마만큼 이루어졌는지 XYZ에 의한 회전에 의해서 회전하게 되면 위에서 보는 것처럼 이러한 Rotation Matrix를 얻을 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (18).jpg){% endraw %}|

대표적으로, 여러분들이 나중에 접하게 될 자이로라던가 기타 각도를 측정할 수 있는 센서들을 통해서 얻게 되는 경우에는
대부분 Rotation Matrix, 또는 Roll, Pitch, Yaw라고 하는 각도를 얻게 됩니다.

## Rotation Matrix로부터 내가 원하는 어떤 값은?

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (19).jpg){% endraw %}|

그러한 Rotation Matrix로부터 내가 원하는 어떤 값은 3가지입니다. 전체적인 Rotation을 표현하기 위한 3가지 값을 얻어내는 것이 필요하게 됩니다. 첫번째로 얻는 것이 $\beta$값입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (20).jpg){% endraw %}|

위에서 보이는 식처럼, arctan라는, 즉 이 위에 보이는 매트릭스의 3번째 줄을 보면 $-sin(\beta)$, $cos(\beta)sin(\gamma)$, $cos(\beta)cos(\gamma)$ 이 값을 이루어서 3번째 줄의 2번째/3번째 요소를 제곱해서 더하게 되면 $\gamma$에 의한 성분은 사라지고, $\beta$에 의한 성분만 나타나게 됩니다.

위에서 보이는 식처럼, arctan라는 즉 위에 보이는 매트릭스의 3번째 줄을 보면 $-sin(\beta)$, $cos(\beta)sin(\gamma)$, $cos(\beta)cos(\gamma)$들이 값을 이루어서 3번째 줄의 2번째/3번째 요소를 제곱해서 더하게 되면 $\gamma$에 의한 성분은 사라지고, $\beta$에 의한 성분만 나타나게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (21).jpg){% endraw %}|

이것은 $arctan의 표현과 어떤 모호성을 제거하기 위해서 컴퓨터 프로그램 상에서 제공하는 식이다. 

$x$와 $y$의 component $x$와 $y$가 어느 축에 존재하는지 즉 $\pm$로 어느 축에 존재하는지에 따라서, arctan라고 하게 되면, ±90도 사이에서 정의되기 때문에 90도일 경우에는 불연속이 발생하는 것을 확인할 수 있습니다. 따라서, 어떤 각도를 표현하는 데에 있어서 일반적인 arctan를 취하면 모호한 값이 나오는 경우가 있어서 이를 방지하기 위해, arctan2는 정확하게 1,2,3,4분면의 각각의 포지션을 즉 X방향, Y방향에 대해서 정확하게 $\pm$인지를 확인해서 각도에 대한 모호성을 없앤 어떤 수식 명령어라고 보면 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (22).jpg){% endraw %}|

그래서 arctan2라는 것을 통해서 $\beta$ 값을 찾아낼 수 있게 되고 이렇게 $\beta$ 값을 찾아내게 되면 이 $cos(\beta)$가 0이 아니라는 가정 하에서 우리는 이 $\beta$값들을 활용해서 1번째 column과, 3번째 row을, 다시 잘 조합함으로서 arctan2 라는 명령어를 활용해서, $\alpha$와 $\gamma$를 역시 똑같이 옆에 보이는 식처럼 얻어낼 수 있게 됩니다.

즉, $cos(\beta)$가 0이 아니라는 조건하에서 이렇게 얻어진 Rotation Matrix를 통해서 $\beta$값을 먼저 얻어내고
그 $\beta$값을 활용하고 $cos(\beta)$가 0이 아니라는 전제 조건 하에서 $\alpha$와 $\gamma$를 얻어내게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (23).jpg){% endraw %}|

그런데 만약에, 이 $\beta$가 $\pm$90도일 때 $cos(\beta)$가 결국 0이 되기 때문에, 앞서서 살펴본 것처럼 $\alpha$와 $\gamma$ 값을 얻어낼 수 없게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (24).jpg){% endraw %}|

비행기에서 $\beta$ 값이 0이라는 의미는 비행기가 완전히 하늘을 향하거나 완전히 바닥을 향하는 경우 이렇게 놓여져 있을 때 $\beta$값은 -90도, 또는 90도로 나타나게 됩니다.

## 짐벌락(GimBal Lock)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (25).jpg){% endraw %}|

이렇게 주어졌을 경우에, 흔히 다른 영역에서는 보통 이것을 ‘GimBal Lock’이라고 말합니다. 이 GimBal Lock에서는 2개의 축이, 이 베타각 ±90도 이루어짐으로서 $x$축에 대한 회전과 $z$축에 대한 회전이 겹치는 경향이 생기게 됩니다.

이 $x$축에 대한 회전과, $z$축에 대한 회전이, 겹쳐버리기 때문에, 2개의 회전이 하나로서 표현되는 것이 아니라 각각에 대한 $\alpha$, $\gamma$에 대한 회전의 합에 의해서 회전한다. 즉, 회전 자체가 조금 모호해지는 그러한 단점이 발생하게 되는게 바로 ±90도가 $\beta$값에서 얻게 되는 때에 발생하게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (26).jpg){% endraw %}|

그래서, 그렇다면 이러한 단점들 때문에 Euler Angles을 사용할 수 없느냐 하면 사실 일반적으로 많은 경우에서 여러분들이 응용해서 사용하는 경우에서는 $\beta$ 값이 ±90도가 되는 경우가 드물 겁니다.
다음에, 여러분들이 Moving Platform, 즉 움직이는 비행기나 수중 Platform을 다룰 경우 금방 말씀드린 이 $\beta$값이 90도가 되는 경우가 충분히 발생할 수 있기에 주의해야겠지만
일반적인 Robot Manipulator에서는 $\beta$값이 ±90가 되는 경우는 그다지 많지 않기 때문에 이에 대해서는 크게 신경쓰지 않아도 좋을 것 같습니다

## Roll, Pitch and Yaw Angles

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (27).jpg){% endraw %}|

ZYX, XYZ, 이런 식의 표현법보다는 일반적으로 Roll, Pitch and Yaw Angles 즉, 위에 보이는 식처럼, $R_z$, 즉 $z$축에서의 $\psi$만큼의 회전, $y$축에서의 $\theta$만큼의 회전, $x$축에서의 $phi$만큼의 회전 이런 연속적으로 이루어진 방식 즉 ZYX의 이 방식을 따르는 것을, Roll pitch Yaw Angles에 의한 Euler Angles 표현법이라고 설명합니다.

## Euler's Theorem

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (28).jpg){% endraw %}|

이 3가지의 회전에 대해서 어떤 2개의 프레임이 존재할 때, 어떻게 $x$축, $y$축, $z$축으로 회전을 했을 경우에 2개를 일치시킬 수 있다, 라고 하는 게 Euler Angles이라고 말했었는데,
이 Euler's Theorem라는 것은 한번의 회전으로 한 프레임에 대해서 다른 프레임으로 갈 수 있는 방법이 있다 라고 하는 것이 Euler's Theorem 입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (29).jpg){% endraw %}|

그래서, 이 Euler's Theorem라 하는 것은 어떠한 임의의 한 축에 대해서 그 축을 찾을 수 있고 그 축에 대해서 회전하는 각도만큼만 확인할 수 있다면 그 2가지의 축과 회전하는 각도에 의해서 한 프레임에서 다른 프레임으로, 한번의 회전으로 갈 수 있다는, 어떻게 보면 한번의 회전으로 2개의 축을 일치시킬 수 있다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (30).jpg){% endraw %}|

반면에, 이 회전하는 축을 찾아내는 보통 $\lambda$라는 하는 이 축을 찾아내는 것은 항상 쉽지만은 않기 때문에 이 표현법에 대해서 수학적으로 접근하는 데에 있어서는 매력적일 수 있는데 반대로 실용적인 면에서는 이 축을 정확하게 찾아내기는 어렵기 때문에 그다지 실용적이지는 않다는 것을 유념해야 합니다.
그래서 이러한 축을, 일반적으로 $\lambda$ 라고 말하고, 이 $\lambda$를 eigen-axis 아니면 오일러가 찾아냈기 때문에 Euler axis라고도 합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (31).jpg){% endraw %}|

이 회전축에 대해서는 $\lambda$라고 말하고 이 회전축이 얼마만큼 회전했느냐를 $\delta$라고 해서 이를 Euler Angle, Principal Euler Angle이라 말합니다,
이렇게 $\delta$와 $\lambda$를 통해, 즉 $\lambda$라고 하면 벡터기 때문에 3개의 파라미터를 갖습니다. 거기에 추가적으로, 이 $\delta$만큼의 각도를 가지고 표현하는 이 4가지 파라미터로 표현하는 것을 quaternion 표현법이라고 말합니다.

## Quaternion 표현법

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-3 (32).jpg){% endraw %}|

이 Quaternion 표현법 같은 경우에는 명확하게 한 축과 돌아가는 각도를 통해 설명하기 때문에 앞서서 설명했던 어떤 표현법에 있어서의 2가지의 각도 표현법이라는 어떤 중복성 문제라던가 또는 아까 말씀드린 $y$축에 대해 ±90도의 값을 통해 GimBal Lock이 생긴다는 문제점을 해결할 수 있는 좋은 방법이기 때문에 Quaternion 표현법도 각도를 표현하는 데에 있어서 많이 사용되는 방법 중 하나입니다.







































