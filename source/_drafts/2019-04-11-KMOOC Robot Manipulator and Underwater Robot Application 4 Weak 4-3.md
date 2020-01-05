---
title: "Robot Manipulator and Underwater Robot Application 4주차 4-3 D-H notation"
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
last_modified_at: 2019-04-11
comments: true
mathjax: true
classes: wide
---

## D-H notation

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3.jpg){% endraw %}|

D-H parameter라고 하는 것은 1955년도에 Denavit교수님과 Hartenberg교수님께서 만드신 `notation'으로
지금까지도 로봇기구학에서는 golden standard로 표현될 만큼 계속해서 사용되고 있는 표현입니다. 

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (2).jpg){% endraw %}|

Denavit-Hartenberg notation이라고하는 것은 systematic하게, 즉, 어떤 로봇이 주어졌을때 그러한 로봇이 주어진 상태에서 어떻게 좌표축을 설정하고
그 좌표축 간의 관계는 어떻게 표현을 하고, 그랬을때 그 표현법에 의해서 원하는 'Homogeneous Transformation'을 어떻게 생성하는지를
자동화하는, systematic하게 표현하는 기법을 의미합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (3).jpg){% endraw %}|

D-H notation은 몇가지 과정과 그리고 설정이 필요합니다. 

첫째, 만들어 놓은, 또는, 만들고 싶은, 해석하고 싶은 manipulator가 있다면 이러한 manipulator는 n+1 link로 구성이 된다.
앞서서 3자유도 로봇 같은 경우에는 3개의 joint와 3개의 link로써 구성이 되어있다고 했는데 여기서는 n+1 link로 표현을 하는데요.
지구상에 보통은 로봇들이 발을 디디고 있어야 됩니다. 그래서 고정되어 있는 바닥을 하나의 link라고 표현을 해서 총 n+1개의 link를 가지고 있다. 라고 얘기를 합니다.
그리고 그 link와 link 사이 base link와 로봇, 그 중간에 하나의 joint가 들어가고 총 n개의 joint들을 가지고 n+1개의 link들을 연결하고 있다. 라고 하는 그러한 과정을 사용을 하고 있습니다.
그리고 각각의 링크에는 좌표계를 하나씩 붙일 것입니다. 그리고 그 좌표계가 각각의 링크마다 좌표계가 하나씩 붙어있다라는 이러한 과정을 통해서 그 좌표계 상에서의 변환을 통해서 끝점의 위치라던지 아니면 또 로봇상의 중간에 어떠한 점이라도 상관없습니다. 그러한 점의 위치를 찾아내기 위해서 활용할 예정입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (4).jpg){% endraw %}|

그러면 이러한 과정을 바탕으로 framework을 한번 설명을 드릴 필요가 있을것 같은데요.
기본적인 D-H parameter를 잡기 위해서는 가장 중요한 것은 Z축입니다.
일단은 Z축을 잡는 가장 기본적인 방법은 joint i+1 번째에 위치시키는 것을 원칙으로 합니다.
즉, 여러분들은 i 번째의 joint에 i번째 frame을 잡는 것이 아니라 i+1 번째의 joint에 i번째의 frame이 되는 것입니다.
예를들면, 첫 번째 joint가 있다면 0번째 frame이 붙게 되는 것입니다. 이 부분을 혼동을 하면 안됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (5).jpg){% endraw %}|

이렇게 i번째 frame에다가 $Z_1$ 축을 잡았다고 했을 때 $Z_i$번째 원점이 존재했을 때 그 다음으로 필요한 것은 $Z$축과 관계되는 $X$축과 $Y$축을 잡아줘야 되는데
이 $X$축을 결정하기 위해서 필요한 것은 이전 축입니다. 즉, $i$번째 축을 가지고 있는데 이전에 i-1번째 축은 어떻게든지 만들었다라고 가정을 한다면, 그 만들어진 축에서 이 i축, 즉 i-1번째 축에서 i축을 연결하는, i축의 Z축을 연결하는 공통의, 공통으로 수직되게 연결될 수 있는 하나의 선을 정할 수 있게 됩니다. 

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (6).jpg){% endraw %}|

그렇게 선을 정하게 되고 그렇게 선을 정한 상태에서 이 공통 수직선을 보통 common normal방향이라고 하는데
이 common normal방향을 $X_i$축으로 설정하게 되는 것 입니다.
즉, joint i + 1 번째의 $Z_i$축을 설정하게 되는 것 입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (7).jpg){% endraw %}|

Z축을 잡았고요 또 Z축과 Z축이 존재했을 때 두 개의 common normal 방향으로 X축을 잡습니다.
이렇게 잡고나면 두개의 축이 결정되면 나머지 축은 오른손 법칙에 따라서 Y축은 자동적으로 결정되게 되는것이죠. 그래서 여러분들은 Y축에 대한 고민을 하실 필요가 없으시고요.
Z축을 어떻게 잡는지 그리고 그 Z축에 대해서 X축을 어떻게 결정하는지만 잘 기억해 두시면 되겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (8).jpg){% endraw %}|

그렇다면 'D-H notation'에서 어떻게 Z 축을 잡는지에 대해서 한번 그림을 통해서 살펴보도록 하겠습니다.
로봇을 활용할 때 주로 활용하는 로봇의 조인트는 전부 다 Revolute joint 아니면 Prismatic joint가 거의 대부분입니다.
물론 이 외의 joint들에 대해서는 어떻게 기술할 것이냐 물론 그런 것들에 대한 방안들도 있지만 일반적으로는 Rotational하는 Revolute joint와
translational하는 Prismatic joint 이 두가지 joint가 거의 모든 로봇, 90%, 아니면 99% 이상 로봇들에서 다 활용이 되고 있습니다.
그렇기 때문에 D-H parameter, 특히 1955년도에 이 개념을 만들 당시에는 이 두가지만 가지고도 충분히 설명이 가능하지 않겠냐 라고 해서 이 개념을 만들기 시작했던 것이고
그 개념이 사실상 지금까지도 그렇게 크게 위배되지 않게 사용되고 있기 때문에 D-H parameter가 아직까지도 널리 이용되고 있다고 보면 되겠습니다.
그러면 이 Rotational한 Revolute joint축에 대해서 Z축을 회전축에 대해서 잡아주자.
회전하는 축을 기준으로해서 Z축을 잡아주자 라고 하는 것이 기본적인 rotation하는 joint에 대한 Z축 방향이 됩니다.
그리고 그 다음에 translational하는 경우에 대해서는 바로 이동하는 방향에 대해서 Z축을 잡아줍니다.
그러면 두 가지의 개념을 두 가지의 joint에 대해 살펴보자면 각각 Z축은 이동하는, 회전을 한다고 하면 결국은 회전하는 방향에 대해서 Z축을 잡아주는 것입니다,
그리고 Prismatic joint, translational하는 이러한 Prismatic joint에 대해서도 역시 마찬가지로 이동하는 방향에 대해서 역시 Z축을 잡아준다.
이렇게 Z축을 잡아주는 방법은 두가지 방법으로 나눌 수 있다는 것을 기억해두시면 되겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (9).jpg){% endraw %}|

축을 어떻게 잡는지에 대해 설명을 드렸는데요. 그 다음에 필요한 것이 X축을 정하는 것이 되겠습니다. 그래서 X축을 정하는 방법은 조금전에 말씀드렸던 것처럼
$Z_{i-1}$번째 축에서 $Z_i$축까지를 연결하는 공통으로 수직하는 line. common perpendicular상으로 결정하기만 하면 X축을 잡아주게 되는 것입니다.
그래서 이 위에 있는 그림처럼 $Z_i$축과 $Z_{i-1}$번째 축이 있으면 공통으로 수직되는 그 line만 찾아주면 되는 것이죠. 

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (10).jpg){% endraw %}|

그런데 항상 이 X축을 찾을 수 있는 것은 아닙니다. 

예를 들어서 0번째 frame에 대해서 Z축을 결정할 수 있습니다.
X축을 결정하기 위해서는 $Z_{n-1}$번째 축이 존재해야 합니다. 그렇지만 우리는 0번째 frame부터 시작하기 때문에 $Z_{n-1}$번째 축이 존재하지 않습니다.그렇기 때문에 X축을 결정할 수 없게 됩니다.
그렇지만 0번째 frame은 보통 기준 좌표계를 의미하기 때문에 0번째 좌표계에서의 규칙은 여러분들이 임의로 여러분들이 편한 방법으로 X축을 결정해주면 되는것입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (11).jpg){% endraw %}|

또 이와 마찬가지로 또 이와 비슷한 개념으로 마지막축일 경우에는 $Z_n$축 같은 경우,
마지막 축에서는 joint를 가지고 joint를 Z축을 잡아주게 되는게 마지막 $Z_n$축 같은 경우에는 joint가 존재하지 않습니다.
즉, link의 끝점이 될텐데. 끝점일 경우에는 조인트가 존재하지 않기 때문에 Z축을 결정할 수가 없습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (12).jpg){% endraw %}|

그래서 일반적으로는 두가지 방법을 많이 쓰고 있는습니다. 

한가지 방법으로는 바로 이전 축의 Z축. 즉, $Z_{n-1}$번째 축과 같은 방향으로 $Z_n$축을 잡아주는 경우

두번째 방법으로는 보통 마지막 joint 같은 경우는 일반적으로 end-effector, 마지막에 있는 손가락이 될 수도 있겠고 집게가 될 수 있겠고 이러한 포인트에서 point out하는 방향,
즉, 밖으로 향하는 방향으로 잡아주는 경우도 있습니다.

그것들도 역시 마찬가지로 여러분들이 필요에 따라서 결정을 하면 되는 것입니다. 그래서 앞서서 X, 첫번째 $X_0$축을 결정할 때는 즉 $Z_{n-1}$번째 축에 있기 때문에 결정할 수 없게 되는 것입니다

마지막축인 경우에는 역시 마찬가지로 마지막 축에는 joint가 존재하지 않기 때문에 축을 결정할 수가 없으니 arbitrary하게 여러분들의 입맛대로 결정하면 되는 것입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (13).jpg){% endraw %}|

그 다음에는 만약에 Prismatic joint라고 생각을 해보셨을 때,
Prismatic joint라고 하면 translational하는 joint가 되는데 이동하는 방향이 양쪽 방향 다 이동할 수가 있습니다.
그렇기 때문에 이 경우에 Prismatic joint같은 경우에도 Z축은 방향은 위쪽 아니면 아래쪽인데, 벡터는 결정이 되지만 벡터의 방향은 위쪽과 아래쪽 이 두개로 나눠질 수 있게 때문에
그 경우는 일반적으로는 로봇이 링크로 연결되다 보면 Prismatic joint가 중간에 들어가면 Prismatic joint가 늘어나는 방향으로 Z축의 방향을 보통 설정 하는데
반대 방향에 경우 필요에 따라서 그렇게 설정을 하더라도 무리가 없습니다. 여러분들이 여러분들 입맛대로 여러분들이 원하는대로 그렇게 설정해주시면 되겠습니다

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (14).jpg){% endraw %}|

그 다음으로 D-H parameter를 구하기 위해서 하나씩 rotation을 전개하다 보면 Z축과 $Z_{i-1}$의 Z축이 이렇게 두개가 교차하는 경우와 평면상에서 교차하는 경우.
대부분 다 수직으로 교차를 많이 할텐데 수직으로 교차하는 경우가 생깁니다.
이럴 경우에는 이 두 축에 대해서 수직인 방향은 바로 이 두개의 축이 형성하는 평면에 대해서 나오는 이 평면의 법선 방향으로 나오는 이 축이 됩니다.
그래서 Z축과 $Z_{i-1}$ 번째 축이 교차할 경우에는 이 X축은 평면에 대해서 수직으로 나오는 방향. 그런데 이 수직으로 나오는 방향은 위로 나올 수도 있고 아래로 나올 수도 있습니다.
그렇기 때문에 역시 마찬가지로 위든 아래든 여러분이 원하시는 방향으로 X축을 정해주면 됩니다.
그렇지만 일반적인 방법으로는 $Z_{i-1}$ 번째 축에서 $Z_i$축으로 이렇게 손가락을 감쌌을때 엄지손가락이 향하는 방향쪽으로 일반적으로 많이 잡아줍니다. 그렇지만 반대로 잡는다고해서 틀린 방법은 아닙니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (15).jpg){% endraw %}|

그 다음으로 만약에 Z축이 서로 수평으로 놓여있을 때, 즉 $Z_{i-1}$번째와 $Z_i$축이 수평으로 이루어질 경우에는 두개를 연결하는 수직선, 두개를 공통으로 연결하는 common perpendicular line이 무수히 많이 존재하게 됩니다.
무수히 많이 존재하게 되기 때문에 우리는 그 중에서 임의로 하나를 설정한 다음에 일반적으로는 원점을 기준으로해서 교차할 수 있도록 보통은 설정해주게 됩니다.
역시 이 위치도 여러분들의 필요에 따라서 바꿀수는 있습니다. 그래서 정확하게 결정되지는 않는다는 그런 단점을 가지고 있습니다.
그리고 마지막 case의 경우 $Z_{i-1}$번째 축과 $Z_i$축이 같은 이런 평행하지만 평행하면서도 아예 같은 방향으로 같이 일치하는 경우가 있습니다.
이경우에는 X축을 어떻게 결정할 수 있을까요? X축은 두개의 common perpendicular인데 X축은 무수히 많이 존재할 수 있습니다.
어떻게 되냐하면 이 축을 감싸고 있는 평면전체가 바로 $Z_{i-1}$번째 축과 $Z_i$축에 모두 수직한 그런 vector가 되기 때문에 이 경우에도 여러분들이 임의로 X축의 방향을 결정할 수 있게 됩니다.
그리고 이 경우에는 조금 후에도 다시 말씀드리겠지만
$Z_{i-1}$번째 축과 $Z_i$축을 두개의 떨어진 거리를 이제 필요로 하게 되는데 그 떨어진 거리도 임의로 원점을 잡아줌으로써 그 거리를 결정하게 되는데
이 원점도 마찬가지로 여러분들이 임의로 여러분들이 편의에 따라서 잡을 수 있게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (16).jpg){% endraw %}|

어떻게 보면 이렇게 모호성을 많이 가지고 있는 방법이 조금 복잡하다 느끼실 수도 있겠는데 어떻게 보면 이러한 모호성이 여러분들한테 많은 자유도를 줄 수 있다. 라고 생각해 볼 수 있는게 좋을 것 같습니다.
앞서서 Z축하고 X축을 어떻게 잡는지 살펴보았습니다. X축과 Z축을 잡으면 Y축까지 자연스럽게 결정된다고 말씀을 드렸고요,
그렇다면 각각의 joint에 어떻게 좌표계가 설정 되는지가 다 결정이 되었으니깐 그러한 좌표계를 이용해서 D-H parameter를 어떻게 정의하는지도 한번 살펴보도록 하겠습니다.
D-H parameter라고 하는 것은 총 4개로 구성되는데 $\theta$, $d$, $a$, $\alpha$가 되겠고요, 이 중에서 여러분들은 $\theta$하고 $d$를 묶어서, $a$하고 $\alpha$하고 묶어서 한번 생각해 보시면 좋을 것 같습니다.
보통 $\theta$하고 $d$같은 경우는 모두 $Z_{i-1}$축을 이용을 해서 정의를 하기 때문입니다.

그리고 마찬가지로 $a$하고 $\alpha$는 $X_i$축을 기준으로 정의를 하기 때문에 두개씩 묶어서 정의하시는게 이해하시기 좋습니다.
$\theta$ 값 같은 경우에는 $Z_{i-1}$ 축을 기준으로 $X_{i-1}$축으로 부터 그다음 Xi축으로 얼마만큼 틀어져 있느냐, 얼마만큼 각도가 rotation되어 있느냐? 를 설명하는 각도가 되겠습니다.
$Z_{i-1}$축에 당연히 수직인 $X_{i-1}$축과 그라고 $X_i$축을 $Z_{i-1}$축에서 수직되게 결정을 했기 때문에 두 개는 결국엔 $Z_{i-1}$축을 기준으로 회전됐다라고 생각을 할 수가 있는 것이죠.
그래서 그 두 축 사이의 회전을 $\theta$i라고 설정을 하게 됩니다.

그 다음에 $d_i$라고 하는 것은 $Z_{i-1}$ 방향으로 이 $Z_{i-1}$축을 포함하고 있는 i-1프레임의 원점에서부터 그리고 이 $X_i$ 축이랑 만나게 되는 점이 존재하게 될텐데 이 두 점 사이의 거리를 $d_i$라고 결정을 하게 됩니다.
이렇게 $Z_{i-1}$축을 기준으로 두개의 parameter $\theta$하고 $d$를 살펴 보았습니다.

이어서 $X_i$축을 기준으로 $a$하고 $\alpha$에 대해서 살펴보도록 하겠습니다.

$a$라고 하는것은 $Z_i$번째 축을 포함하고 있는 i번째 프레임에서 이번에는 $Z_{i-1}$번축에서부터 i번째 프레임의 원점까지 떨어진 거리를 결국에는 이 떨어진 거리를 $X_i$ 축 방향으로 떨어진 거리를 정의할 수 있는데
두개 사이의 축이 즉, $Z_{i-1}$과 $Z_i$가 수직하기 때문에 그 수직하는 두개 사이의 거리를 결정할 수 있게 되는 것 입니다. 그래서 이 떨어진 거리를 $a_i$라고 설정하게 됩니다.
그리고 마지막으로 $X_i$ 축은 아까전에 정의할때 $Z_{i-1}$과 $Z_i$에 대해서 둘다 수직한 그러한 방향이라고 설정을 했기 때문에 이 $X_i$에 대해서 얼마만큼 회전이 되느냐?
그 각도 회전각도를 $\alpha_i$, $X_i$축에 대해서 $Z_{i-1}$번째 방향에서 $Z_i$방향으로 얼마만큼, $\alpha$만큼 회전이 일어났느냐?
그래서 이 네가지 parameter로서 D-H parameter를 설정할 수 있게 되는 것입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (17).jpg){% endraw %}|

이어서 D-H parameter를 이용을 해서 어떻게 joint간에 그리고 어떻게 frame간에 이 Transformation과 rotation을 만들어 내는지를 한번 살펴보도록 하겠습니다.
네 가지 parameter정의를 했습니다. 여러분들이 먼저 거꾸로 온다고 생각을 해봅시다. 거꾸로 즉 $Z_i$축에서부터 $Z_{i-1}$축. 즉, i프레임에서 i-1번째 frame으로 가지고 오는 것입니다.

즉 i-1번째 프레임에서의 표현되는 이 i번째의 frame에 있는 위치를 설명하기 위해서는 첫 번째로 이 $Z_i$축은 $Z_{i-1}$축에 대해서 $\alpha$만큼 rotation이 되어 있는 것이죠.
그렇기 때문에 먼저 X축 방향으로 $\alpha$를 X축에 대해 정의를 했었습니다.

X축 방향으로 $\alpha$만큼 rotation을 시키고 $X_i$ 축에 대해서 역시 $a_i$ 만큼의 translation했습니다.
그렇기 때문에 translation시키는 Matrix를 이용해서 coordinate(좌표)을 통일시켜줍니다. 그리고 그다음에 한 것이 바로 $d_i$만큼을 $Z_{i-1}$축으로 이동을 시켰습니다.
이 거리만큼을 그래서 이 이동하는 Transformation Matrix를 계산을 해주고 그리고 마지막으로 Z축을 서로 통일시켜주기 위해서 $\theta_i$만큼을 회전을 시켰습니다.
그래서 마지막으로 rotation을 $\theta_i$만큼 회전을 시켜준다면 이 순서대로 거꾸로 rotation translation translation rotation.
이 두개 사이의 위치는 바뀌어도 됩니다. 즉, rotation을 먼저하고 translation을 해줘도 됩니다.
거꾸로 translation을 해주고 rotation을 먼저 해줘도 관계는 없습니다.
이렇게 네 개의 'Homogeneous Transformation'을 활용을 해서 전부다 연산을 취하면 우리는 바로 D-H Matrix라고 하는 이 A Matrix를 찾을 수 있게 되는 것입니다.
그래서 이 각각의 Rotation Matrix와 translation Matrix를 전부 다 이 값들 $\alpha$, $a$, $d$, $\theta$를 집어 넣어서 계산을 하게 되면
아래와 같이 이런 'Homogeneous Transformation'을 얻을 수 있는데 이렇게 생긴 'Homogeneous Transformation'를
1Denavit-Hartenberg transformation 이라고 하게 되는 것 입니다.
이렇게 되면 요 앞에 있는 'Homogeneous Transformation'에서 상위, 이 위에 있는 3 by 3 Matrix는 Rotation을 의미한다라고 했는데요.
즉 $Z_{i-1}$번째 축에서 $Z_i$축을 표현하기 위해서 얼마만큼 rotation되어 있느냐는 결국에는 이 $\theta$와 $\alpha$로써 rotation을 설명할 수 있게 되는 것이고요.
마찬가지로 이 두축 사이에 떨어진 거리. 두 축 사이의 원점 간의 떨어진 거리는 이쪽에 있는 translation하게 되는 벡터로써 표현이 되게 자동적으로 이러한 'Homogeneous Transformation'를 D-H parameter를 이용해서 구성할 수 있게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (18).jpg){% endraw %}|

그렇다면 앞서서 Z축을 잡는데 있어서 Revolute joint와 Prismatic joint에 대해서 두가지 조인트가 존재한다고 여러분께 말씀을 드렸는데
이제 Revolute joint 같은 경우에는 결과적으로는 $\theta$가 앞서서 4개의 파라미터 중에서 $\theta$가 Variable. 변하는 인자가 되겠습니다.
나머지 $d$, $a$, $\alpha같은 경우에는 Constant, 즉 한번 로봇이 만들어지면 이 값들은 변하지 않고 그대로 자기 값을 유지하는 Constant값이 되고요.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (19).jpg){% endraw %}|

마찬가지로 Prismatic joint, 이번에는 Z축 방향으로 $d$가 움직이죠?
$d$가 움직이기 때문에 $d$가 Variable이 되겠고, 마찬가지로 $θ_i$, $a_i$, $\alpha_i$가 Constant값을 갖는 그러한 변수로 여러분들이 이해하시고 적용하시면 되겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-3 (20).jpg){% endraw %}|

앞서서 말씀드렸던걸 요약을 하자면 결국은 Revolute joint에 대해서는 $a$, $d$, $\alpha$라는 값이 고정 값이 되겠고 변하는 값은 회전하는 $\theta$의 값이 되겠습니다.
그리고 Prismatic joint는 $a$, $\theta$, $\alpha$가 역시 Constant값이 되겠고, 그리고 $d_i$ 즉, Prismatic joint의 진행방향으로의 그 값이 변하는 값이 되겠습니다.
그래서 총 각각 어떠한 joint 이던지 간에 3개의 parameter는 고정되어 있고 하나의 parameter만 변하는 그러한 구조를 띄고 있다고 생각하시면 되겠습니다.
