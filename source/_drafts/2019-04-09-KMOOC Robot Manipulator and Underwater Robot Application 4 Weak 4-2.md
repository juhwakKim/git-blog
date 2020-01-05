---
title: "Robot Manipulator and Underwater Robot Application 4주차 4-2 2D-Example"
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
last_modified_at: 2019-04-09
comments: true
mathjax: true
classes: wide
---

## Transform joint coordinates to end-effector coordinates

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-2.jpg){% endraw %}|

위에 보이는 평면상에 3개의 joint와 3개의 link로 구성되어 있는 이러한 평면 3자유도 로봇이 있습니다.

평면 3자유도 로봇이라고 하는 것은 3개의 관절로 이루어져 있기 때문에 3자유도 로봇이 됩니다. 또 3개의 자유도를 가지고 있는 끝점(end-effector)의 위치와 자세까지를 3자유도로 표현이 가능합니다. 관절공간의 자유도 3자유도 그리고 작업공간의 자유도 3자유도로 매칭을 시켜보도록 하겠습니다. 가장 기본적으로 사용하는 수학적인 표현법. '$sin$, $cos$과 관절의 길이($l$)'를 바탕으로 식을 써보면 옆과 같이 표현 됩니다. 즉, $x$는 $x$의 위치, 이 로봇의 끝점에서의 $x$의 위치를 관절공간에서의 자유도인 $\theta_1$, $\theta_2$, $\theta_3$를 이용해서 이 점의 끝을 기술해 볼텐데요. $sin$, $cos$을 활용해서 $l_1cos\theta_1 + l_2 cos(\theta_1 + \theta_2) + l_3cos(\theta_1+\theta_2+\theta_3)$으로 $x$점의 좌표가 위의 식처럼 표현된다는 것을 확인할 수가 있습니다.

마찬가지로 $y$에 대해서는 $sin$방법을 이용해서 $y$의 값들을 구할 수 있습니다.
그리고 끝점에서의 로봇이 위치하고 있는 각도는 결국에는 $\theta_1$과 $\theta_2$, $\theta_3$의 각의 합에 의해서 결과적으로 로봇의 끝점, 끝 방향 이 결정되게 됩니다.

그래서 결론적으로 이 $x$, $y$, $\phi$라고 하는 3개의 공간상의 좌표는 옆에 보 이는 식처럼 $\theta_1$, $\theta_2$, $\theta_3$ 이 세가지 관절공간의 좌표에 의해서 관절공 간의 자유도의 그리고 값들에 의해서 표현이 가능해 지는 것입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-2 (2).jpg){% endraw %}|

그렇다면 이렇게 표현된 방법을 새로운 로봇이 주어진다면 여러분들은 새롭게 주어진 로봇들을 역시 마찬가지로 바로 이전 표현법처럼 각각의 끝점이 어떻게 위치하는지는 $sin$, $cos$ 대부분 아마 $sin$, $cos$으로 표현이 가능합니다.

그래서 $sin$, $cos$을 이용해서 어느점이 어떻게 매칭이 되는지를 식을 구하면 됩니다. 그런데 새로운 로봇을 만들때마다 그걸 전부다 일일이 손으로 푼다는 것은 사실상 쉽지 않은 일입니다. 그래서 이러한 위치 표현법들을 조금 systematic하게 수행하기 위해서 추후에 D-H parameter를 통해서 자동화하는 기법을 살펴볼 예정입니다. 그 전에 앞서서 배웠던 내용들을 바탕으로 어떻게 이러한 이 좌표, 이 끝점에 대한 표현을 '좌표변환'이란걸 통해서 그리고 'Homogeneous Transformation'을 통해서 표현할 수 있는지에 대해서 살펴보도록 하겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-2 (3).jpg){% endraw %}|

다시 앞서 바로 설명해드렸던 예제인 3 link manipulator 평면 3자유도 manipulator를 가지고 설명을 드리도록 하겠습니다.
각각의 길이는 $l_1$, $l_2$, $l_3$로 동일합니다. 그리고 'Homogeneous Transformation' 을 사용하기 위해선 좌표계를 설정해보도록 하겠습니다. 

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-2 (4).jpg){% endraw %}|

위에 그림에서처럼 전체의 manipulator가 고정되어 있는 이 바닥점을 $x_0$와$y_0$, 그리고 $link_1$의 시작점을 $x_1$와$y_1$,$link_2$의 시작점을 $x_2$와$y_2$, 그리고 $link_3$의 시작점을 $x_3$와$y_3$. 이렇게 좌표계를 설정 합니다. 원하는 이 로봇의 끝점을 위에 있는 그림에서 이 노란색점을 끝점의 위치라고 한다면 위치를 정확하게 표현하기 위해서 앞서 배운 Homogeneous Transformation을 통해서 설명을 해본다면 이 끝 점의 위치는 결과적으로 세 번째 좌표계에서 $l_3$
즉, $x$방향으로는 $l_3$위치에 존재하고, $y$방향으로는 0, 그다음에 평면이기 때문에 $z$방향, $z$축 방향으로 0의 위치에 있을 것입니다.

이렇게 $l_3$, 0, 0을 옆에 보이는 식처럼 Homogeneous Transformation H를 찾기 위해서 $l_3$, 0, 0, 1이라는 값을 통해서 결과적으로는 '0번 좌표계에서 어떻게 $x$, $y$, $z$로 표현되느냐?'라는 것을 찾고 싶은 것입니다.
그러기 위해서 전주 차에 배웠던 내용을 바탕으로 하나씩 적용을 해보도록 합시다.
먼저, 이 노란점을 가지고 두 번째 좌표계로 가져오기 위해서 두 번째 좌표계와 각도를 일치시킬 필요가 있습니다.
그리고 두 번째 좌표계와 세 번째 좌표계의 틀어진 각도만큼 회전시킨다라고 볼 수도 있는 것이죠.
그래서 마지막 이 위에 있는 보이는 식처럼 마지막에 있는 $R_z$축 방향으로 $\theta_3$만큼 회전을 하면 결국 이 세 번째 축에 있는 노란색점을 두 번째 축에 있는 두 번째 좌표계의 점으로써 표현을 할 수 있습니다.
그렇게 해서 먼저 $R_z$를 통해서 거꾸로 이 마지막에 있는 $R_z$를 통해서 $\theta_3$만큼 회전을 시키게 되겠고요. 그 다음에 그 회전시켰기 때문에 이제는 두 번째 좌표계에서 표현이 되고 있습니다.
두 번째 좌표계에서 표현이 되고 있는데 이 좌표축 자체가 $l_2$만큼. 이 link, 두 번째 link 길이의 $l_2$만큼 떨어져 있는 것이죠.
9래서 그 $l_2$의 길이만큼 당겨올 필요가 있죠. 그래서 이 두개의 좌표축을 이동시키기 위해서, 다시 말해 이 두가지 좌표계를 일치시키기 위해서 $l_2$만큼 떨어져 있는 것을 translation 시키는 'Homogeneous Transformation'을 이용해서 가지고 올 수 있습니다.

다시, 이제는 두번째 축에서 정확하게 표현이 되고 있으니깐 이걸 다시 첫 번째 축으로 가져 오기 위해서
역시 마찬가지로 rotation, 즉 두 번째 축을 첫 번째 축하고 얼마나 틀어져 있는지를 살펴봐서 즉, $\theta_2$만큼 틀어져 있기 때문에 $\theta_2$만큼 회전을 시키고 다시 $link_1$의 길이만큼 가지고 오고 마지막으로 $\theta_1$, 즉, zero좌표계 이전에 정의한 기존 base frame과 첫 번째 frame, 두개의 기존 좌표계가 틀어져 있는 $\theta$만큼 회전을 시키면 이 노란색 점이 결과적으로는 $x_0$, $y_0$ 상의 어디에 있는 점인지 이러한 관계식을 통해서 살펴볼 수가 있게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-2 (5).jpg){% endraw %}|

어떻게 보면 앞서 나왔던 $x$, $y$, $z$ 각각의 점들을 표현하는 방법들이 더 쉬워 보일 수도 있는데, 조금 복잡해 보일 수 있지만 이러한 방법을 쓰는 이유는 앞으로 자동화하고
어떠한 그 로봇이 설계 되더라도 여러분들은 systematic하게 표현할 수 있는 방법을 배우기 위해서 이렇게 복잡하지만 체계적으로 살펴보았습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-2 (6).jpg){% endraw %}|

이렇게 살펴본 것들을 조금 다른 측면에서 본다면 이번에는 그 노란색 점이 그 세 번째 좌표축의 끝점에 있다라고 생각할 것이 아니라
그 마지막 끝점에다가도 역시 좌표계를, 즉 네 번째 좌표계를 붙인다 라고도 한번 생각해 볼 수가 있겠습니다.
그렇게 네 번째 좌표계를 붙이면 이 노란색 점은 네 번째 좌표계의 원점이 되는 것이죠.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-2 (7).jpg){% endraw %}|

그래서 위에 보이는 식처럼 이번에는 'Homogeneous Transformation'상에서 0, 0, 0, 즉, 원점을 위하는 네 번째 좌표계의 원점을 의미하는 0, 0, 0 이라는 값으로서
0번째 기준 frame에 좌표계로 가져오는 이런 'Homogeneous Transformation'을 만들게 될텐데요.
그러면 새롭게 이렇게 좌표계를 추가함으로써 추가적으로 들어가는 식은 앞서 식에서 여기 마지막 식에서 보이는 것처럼 $l_3$만큼을 translation 시키는 즉, 좌표계 네 번째 좌표계와 세 번째 좌표계가 얼마만큼 떨어져 있느냐 라는 것을 표현하는 $T_{x_3}$는 $l_3$라고 하는 마지막 'Homogeneous Transformation'만 하나 더 추가를 하면 되는 것이죠.
이렇게 추가함으로써 왜 또 한번 더 복잡하게 만드는 것인가라는 의문이 들 수 있는데 이렇게 추가함으로써 이 식을 거꾸로보시면 $TR$ $TR$ $TR$ 이렇게 각각 두개씩 묶어서
즉, translation, rotation, translation, rotation, translation, rotation과 같은 규칙성을 가지고
하나의 좌표축에서 좌표축으로 좌표축에서 좌표축으로의 변환을 systematic하게 표현하기 위한 기본적인 단계를 완성할 수가 있게 되는 것입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA4-2 (8).jpg){% endraw %}|
