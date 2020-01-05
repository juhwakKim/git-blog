---
title: "Robot Manipulator and Underwater Robot Application 3주차 3-1 Robot Kinematics Introduction"
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

## Robot Manipulator 종류

### Open loop manipulator(Serial robot manipulator)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1.jpg){% endraw %}|

Open loop Manipulator라고 하면 위에 보이는 그림처럼 로봇들이 사람의 팔과 같이 하나하나하나 연속해서 serial과 같이 open loop로 연결되어 있는 Manipulator을 지칭합니다.

#### Open loop Manipulator 장점

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (2).jpg){% endraw %}|

#### Open loop Manipulator 단점

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (3).jpg){% endraw %}|

### Parallel robot manipulator

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (4).jpg){% endraw %}|

Parallel robot manipulator 같은 경우에는 각각의 어떤 로봇의 지지체, 구동부를 여러 로봇의 어떤 다리들이 연속적으로, 평행하게 받쳐주면서 구동하도록 하는 로봇을 말한다.

#### Parallel robot manipulator 장점

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (5).jpg){% endraw %}|

#### Parallel robot manipulator 단점

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (6).jpg){% endraw %}|

## 기구학(Kinematics)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (7).jpg){% endraw %}|

직렬형, 병렬형 로봇 매니퓰레이터에 있어서 각각의 링크가 각각의 조인트가 구동됨에 따라서, 끝점, 내가 원하는 어떠한 로봇 팔의 끝점, 작업하는 점이 어떻게 움직이는지에 대한 위치, 속도, 가속도의 측면에서 해석하는 것을 기구학이라고 부릅니다.

## 역기구학(Inverse Kinematics)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (8).jpg){% endraw %}|

Inverse Kinematics, 즉 역기구학이라고 하는 것은, 끝점이 이렇게 움직이기 위해서 각각의 관절들을 어떻게 구동시켜야 되는지에 대한 해석을 하는 것들을 Inverse Kinematics라고 합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (9).jpg){% endraw %}|

## 관절(Joints)의 종류

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (10).jpg){% endraw %}|

### 회전형 관절(Revolute)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (11).jpg){% endraw %}|

모터 하나를 가지고 이러한 회전형 Joint를 구동하는 방식으로 많이 이루어집니다

### 직선형 관절(Prismatic)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (12).jpg){% endraw %}|

유압 actuator에서 가장 많이 사용된다. 

### 회전 및 직선형 관절(Cylindrical)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (13).jpg){% endraw %}|

### Universal & Spherical

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (14).jpg){% endraw %}|

## 구동기의 종류

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (15).jpg){% endraw %}|

## 기구학 해석

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (16).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (17).jpg){% endraw %}|

기구학을 해석하는 데에 있어서 또 한가지 알아볼 필요가 있는 것은 어떻게 조인트들의 움직임을 로봇에서 구현할 수 있는지 또는 알아낼 수 있는지에 대한 것들을 살펴보는 것이다.

이 관절들이 얼마만큼 구동되는지 알아야 순기구학, 즉 끝점이 어딘지를 알아낼 수 있기 때문에, 이러한 관절들의 움직임을 정확하게 측정할 필요가 있습니다.

### 관절 각도 측정(Sensing angular displacement of a joint)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (18).jpg){% endraw %}|

#### Resolver, RVDT

대표적인 관절각도 측정 장치로는 Resolver, RVDT가 있고 모터가 돌아갈 때 일종의 발전의 원리로서

모터가 빨리 돌아가거나, 아니면 어느 정도의 위치에 돌아갔을 경우에 그 값을 그 전류값을 통해서 모터가 얼마만큼 돌아가는지를 측정하는 방식의 어떤 센서가 되겠습니다.

#### Potentiometer, Rotary Encoder

거의 모든, 여러분들이 모터를 사용하는 어떤 어플리케이션이라고 생각한다면, 거의 모든 관절에는 Rotary Encoder가 포함되어 있다고 보면 되겠습니다.

### Optical Encoder

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (19).jpg){% endraw %}|

위에 나오는 그림처럼, 이렇게 Encoder 같은 경우에는 얇은 판에 구멍이 뚫려있고, 그 구멍 주변을 중심으로 앞뒤로, 한쪽에서는 발광, 한쪽에서는 수광하는 센서장치가 놓여있게 됩니다. 그래서, 발광하는 센서를 통해서, 만약에 모터가 돌아가게 되면, 많은 구멍이 뚫려 있는 판이 돌아가면서, 빛이 들어왔다, 안 들어왔다를 반복하게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (20).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (21).jpg){% endraw %}|

이렇게 빛이 들어왔다가, 안 들어왔다를 반복하는 그러한 판에,
보통 2가지의 신호를 받을 수 있도록, 2개의 구멍을 팠을 때, 보통 A상과 B상, 즉 A시그널과 B시그널을 약 90도 간격으로 어긋나게 배치함으로서,
어느 쪽 엣지가 먼저 신호가 발생하는 지를 판단해서, 방향을 읽어낼 수 있고,
그리고 더 정밀하게, 즉 막혀있는 구멍이 100개, 뚫려있는 구멍이 100개라고 한다면, 전체적으로 총 200번으로 전체 구간을 나눌 수 있을 겁니다.
그런데, A와 B처럼 이렇게 약간씩 어긋나서, 0과 1이 반복되는 것을 어긋나게 했을 경우에는 A와 B의 각각에 대한 값들에 대한 조합으로,
100개의 구멍이 있다고 했을 때, 총 400번으로 1바퀴를 나눠볼 수가 있을 겁니다.
그렇기 때문에, Optical encoder를 통해서, 이러한 방식으로 모터가 돌아감으로서, 얼마만큼 돌아가는지를 측정할 수 있게 되는 것이죠.

#### Optical Encoder의 종류

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (22).jpg){% endraw %}|

가장 많이 쓰는 것은, 증분령, 즉 Incremental Rotary Encoder 입니다.

Incremental Rotary Encoder는 전기가 입력되는 순간, 즉 모터와 Encoder의 외부에서의 어떤 전원이 인가되는 순간부터 측정을 시작하게 됩니다.

즉 전원이 인가되는 순간부터, 내가 어떤 방향으로, 앞인지 뒤인지, 몇번의 펄스가 뛰었는지를 측정해서,
내가 앞으로 얼마만큼, 뒤로 얼마만큼 돌았다는 것을 측정하는 방식이, 바로 Incremental Rotary Encoder 방식이 되겠습니다

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (23).jpg){% endraw %}|

Absolute 방식의 경우 전원을 인가하는 순간, 그 순간은 일반적인 Incremental Rotary Encoder 방식의 경우에는 2개의 구멍만이 파여 있는데, Absolute 방식의 경우에는, 필요에 따라서, 보통은 5개 이상, 5개~6개의 층으로 나누어진, 구멍이 뚫린 판으로 이루어져 있습니다. 위의 그림처럼, 이렇게 뚫려 있을 경우에는, 내가 어느 위치에 딱 존재하는지를 바로 알아낼 수 있는, 즉 이 구멍의 조합으로서, 5개 이상, 또는 많게는 10개까지, 이러한 구멍의 조합이 나타나게 되면, 그 조합에 의해서, 내 위치를 정확하게 알아낼 수 있다, 라는 그런 장점을 가지고 있습니다.

#### Absolute Encoder, Incremental Rotary Encoder의 장단점

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (24).jpg){% endraw %}|

Absolute Encoder가 훨씬 더 사용하기가 편하다는 생각을 할 수 있지만 Incremental Rotary Encoder를 더 많이 사용한다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (25).jpg){% endraw %}|

Absolute Encoder 같은 경우에는, 그 편리성, 즉 순간 내가 어느 위치에 있는지를 정확하게 알 수 있다는 장점을 가지고 있지만, 반면에 10개의 구멍, 11개의 구멍, 12개의 구멍을 가지고 정확하게 알아내기 위해서, 즉 정밀하게 하기 위해서는, 그 구멍들의 개수가 늘어나야 할 텐데, 늘어나는 순간, 그 구멍들의 정보들을 전부 다 전달받아야 합니다.
그렇기 때문에, 10개, 11개, 12개, 13개, 늘어나는 만큼, 신호 시그널을 받아내기 위한 선들의 숫자가 증가하게 되는 것이죠.
즉 선이 굉장히 많이 필요하게 됩니다.

13개, 14개의 선의 경우, 보통 로봇을 만들기 위해 6개 이상의 모터를 사용하는데, 그 로봇의 6개의 모터를, 전부 다 이런 식으로 12개 이상의 선을 사용한다면, 로봇이 선으로 뒤범벅이 될 수밖에 없습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (26).jpg){% endraw %}|

두번째로는, 정밀도를 높이는 데에 있어서, 구멍의 수를, 10개, 12개, 13개, 14개 이렇게 증가시켜나가는 것인데, 이렇게 계속해서 무한정 늘려나가는 것은 어려움이 많습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (27).jpg){% endraw %}|

Incremental Rotary Encoder는 전기가 딱 가해지는 순간부터 측정이 가능하다는 것 외에는, 전기가 가해지는 순간부터, 보통 몇 바퀴 돌아가는지에 대한 것들을 구멍의 개수만큼으로 측정할 수 있습니다. 

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (28).jpg){% endraw %}|

구멍을 조금 작게 뚫는 것들은, 요즘에 많은 정밀 가공 기술들로 인해서 그렇게 비교적, 구멍의 종류를 늘리는 것들에 비해서, 조금 더 쉬운 일입니다. 그래서 정밀도를 증가시키기 위해서는, 이 구멍의 개수를 늘리는 것이 그렇게 어렵지 않기 때문에, 관절 각도 측정을 하는 데에 있어서는, Incremental Rotary Encoder의 정밀도를 높이면서 활용하기에는 좋다는 장점을 갖고 있습니다. 

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (29).jpg){% endraw %}|

그렇지만, 단점은 아까 말씀드렸던 것처럼, 초기에, 내가 어느 위치에 있는지를 정확하게 알기가 어렵다는 점입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (30).jpg){% endraw %}|

그래서 보통은 외부에서 측정할 수 있는, 리미트 스위치, 또는 근접 스위치 같은 것들을 통해서 초기화 시켜준다.

### 말단 장치의 오차 수정 방법

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (31).jpg){% endraw %}|

모터들의 오차가 쌓이게 되면, 그리고 센서들의 오차도 쌓이게 되면 각각의 하나하나의 오차들이 마지막 끝단에서는 크게 나타날 수도 있습니다.

그렇기 때문에, 그 말단 장치, 맨 마지막 장치에는 오차가 크게 나타날 수가 있어서, 각각에 달려있는 Encoder, 즉 관절 측정장치와는 별도로, 말단 장치에서의 위치와 각도를 측정할 필요가 있을 수도 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (32).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (33).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-1 (34).jpg){% endraw %}|













