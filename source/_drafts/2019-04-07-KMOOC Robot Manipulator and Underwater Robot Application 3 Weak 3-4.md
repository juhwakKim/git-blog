---
title: "Robot Manipulator and Underwater Robot Application 3주차 3-4 Euler Angles(2)"
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

## Euler's Theorem

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4.jpg){% endraw %}|

$\lambda$라는 축을 찾았다고 가정해보자, 이 축에 대해 완벽하게 한번만 회전한다면 회전을 이룰 수 있다 라고 했을 때, 이 $\lambda$를 우리가 가지고 있는 $z$축과 일치시키면 그 $z$축에 대해서 마지막에서 회전을 하고 다시 일치시킨 것을 거꾸로 되돌아온다면 그 $\lambda$라는 축에 대해서 $\delta$만큼의 회전을 충분히 쉽게 표현할 수 있을 겁니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4 (2).jpg){% endraw %}|

이 방식을 오일러가 제안한 방법대로 위에 있는 그림에서 1번으로 먼저 $x$축에 대해서 $\alpha$만큼 회전하고 다시 2번째로 $y$축에 대해서는 $-\beta$, 즉 돌리는 방향이 반대입니다.
그렇기 때문에, $y$축에 대해서 $-\beta$로 가지고 오게 되면 $\lambda$가 $z$축과 일치하도록 위치시킬 수 있게 됩니다. 이 상태에서 이 $z$축에 대해서 $\delta$만큼 회전을 하는 것은 $\lambda$에 대해서 $\lambda$만큼 회전하는 것과 같은 표현법이 되겠습니다. 이렇게 표현해서 바꿔서 회전한 다음에 다시 원래대로 거꾸로 돌아갑니다. $y$축에 대해서, 아까는 $-\beta$만큼 회전했기 때문에, 이번에는 $+\beta$만큼 회전하고 다시 $x$축에 대해서 $-\alpha$만큼 회전하게 된다면 람다에 대해서 $\delta$만큼 회전하는 것을 이렇게 5번의 로테이션으로 5개의 로테이션으로 나누어서 2 방법의 일치성을 찾아볼 수 있게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4 (3).jpg){% endraw %}|

이렇게 5개의 회전을 위에 보이는 수식처럼 차례대로 기술해보았습니다. $x$축에 대한 $\alpha$만큼의 회전 다시 $y$축의 $-\beta$만큼 회전 $z$축에 대해서 $\delta$만큼 회전, $y$축에 대해서 $\beta$만큼 회전 다시 $x$축에 대해서 $–\alpha$만큼 회전 이런 식으로 5가지 로테이션 매트릭스로 오일러 정리라고 불리는, $\lambda$에 대해서 $\delta$만큼의 회전을 이렇게 표현해보았습니다. 조금 수식이 복잡하기 때문에 약간씩 약어를 써서 $v\delta$라고 하는 것은, $1-cos\delta$라는 것으로 표현했고 이런 식으로 5가지 매트릭스를 1개의 식으로 썼을 때 이렇게 매트릭스로 으;에 보이는 매트릭스대로 나오는 것을 확인할 수 있습니다. 

## Rodrigues'formula

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4 (4).jpg){% endraw %}|

이 복잡해 보이는 것을 Identity Matrix와 그리고 skew-symmetric matrix, 그리고 $\delta$, $sin\delta$, $cos\delta$의 값을 이용해서 위와 같은 값으로 나타낼 수 있게 됩니다.

이렇게 식으로 나타내는 것을, 바로 Rodrigues'formula라고 말합니다.

이렇게 오일러 정리를 나타내는 매트릭스의 조합을 이와 같은 수식으로 표현할 수 있습니다.
이렇게 Rodrigues'formula가 주어지고 여기에서 $\lambda$가, 아까 말했던 Euler axis가 되겠고,
그리고 $\lambda$의 옆의 곱하기 표현된 것이 매트릭스에서 살펴본 skew-symmetric matrix를 만든 것과 같은 식입니다.
그렇게 $\lambda$ 옆에 곱하기 표시가 있는 것은 $\lambda$를 이용한 skew-symmetric matrix, cross product를 만들기 위한 skew-symmetric matrix를 표현한 것과 같고
$[\lambda X]^2$은, 계산해 보면, $\lambda\lambda^T-I_{3X3}$ 라고 하는 것으로 얻어진다는 것을 확인할 수 있게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4 (5).jpg){% endraw %}|

그래서, 최종적으로, Rodrigues'formula를 이렇게 얻어지는 것을, 앞서서의 식으로서 충분히 설명이 가능하다, 단순한 식으로 이렇게 간단하게 표현할 수 있다는 것을 살펴봤습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4 (6).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4 (7).jpg){% endraw %}|

일단은 우리는 매트릭스가 주어지게 되면 그 매트릭스로부터 알고 싶은 것은 얼마만큼의 회전이 이루어졌는지에 대한 그 회전량, 즉 $\delta$가 되겠고 그 다음에 어느 축에 대해서 회전이 이루어졌는지 그 축에 대한 $\lambda$ 라고 하는 그 축을 얻고 싶을 겁니다. 이랬을 때 이 Rodrigues'formula를 통해서, 3 by 3 매트릭스를 가지고 있었을 때 그 매트릭스의 각 인자들을 각각 $r_{32}$, $r_{23}$, $r_{11}$, 이런 식으로 명명했을 때 그 값들을 이용해서 옆에 보이는 식처럼 $tan\delta$는 이와 같은 식으로 $tan\delta$를 정의할 수 있고 이렇게 얻어진 것을 $arctan\delta$를 취해서 $\delta$를 얻게 됩니다. 역시 이렇게 얻어진 $\delta$를 활용해서 옆에 보이는 $\lambda$를 구하는 식
즉 $1 \above 1pt 2sin\delta$을 곱한 다음 $r_{32}$에서 $r_{23}$을 빼고, $r_{13}$에서 $r_{31}$을 빼고, 이런 식으로 각각의 파라미터 값을 가져와서 빼게 되면 $\delta$와 $\lambda$를 얻을 수 있게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4 (8).jpg){% endraw %}|

이러한 Rodrigues'formula에서 대표적으로 $z$축에 대한 회전도 역시 Euler's Theorem 에서 어떤 2가지의 두 프레임은 무조건 어떠한 이 회전하는 축과 그 회전하는 축에 대한 일정한 각도, 이 2가지로 표현이 가능하다라고 했는데 이 2가지 표현을 $z$축에 대한 로테이션, 이 역시 마찬가지로 성립해야 하기 때문에 이와 같이, $z$축에 대한 $\theta$만큼의 회전 매트릭스, 즉 $cos\theta$, $-sin\theta$, 0,  $sin\theta$, $cos\theta$, 0, 0,0,1 로 되어 있는 이러한 $z$축에 대한 $\theta$만큼의 회전 매트릭스에서 먼저 $tan\delta$를 뽑아내게 되면 앞서서의 formula를 그대로 사용하게 되면 $2sin\theta \above 1pt 2cos\theta$, 즉 $tan\theta$가 얻어지게 되고 이 $\delta$와 $\theta$가 같다, 즉 $\delta$가 $\theta$가 된다는 것을 확인할 수 있습니다. $\lambda$는 $ 1 above 1pt 2sin\theta$인데 앞서서의 수식을 그대로 적용하게 되면 0,0,$2sin\theta$라는 것을 얻을 수 있게 됩니다. 그래서, 결과적으로는 0,0,1, $z$축에 대해서, $z$축은 0,0,1로 표현됩니다 $z$축에 대한 $\theta$만큼의 회전으로서 Rodrigues'formula가 그대로 성립한다는 것을 예제를 통해 살펴볼 수 있었습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4 (9).jpg){% endraw %}|

앞서서, 어떤 로테이션 같은 경우에는 ‘commute하지 않다’, 즉 로테이션은 순서에 따라서 어떤 식을 먼저 돌리느냐에 따라서 결과값이 달라진다고 했습니다.

그렇지만, 로테이션 매트릭스가 굉장히 작은 로테이션만큼 이루어졌을 경우에는 그 로테이션끼리는 서로 commute하게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4 (10).jpg){% endraw %}|

무슨 말인고 하니 만약에  $R_1$로테이션을 $x$에 대해서 $\delta_1, $\delta_1은 굉장히 작은 값이라는 의미입니다.
이 $\delta_1$만큼의 회전이 이루어졌을 때 옆에서 보는 것처럼 $x$에 대한 회전에서 $cos $sin이 $\delta$ 값이 굉장히 작을 경우에는 $cos$은 1로 수렴하게 되고, $sin$은 $\delta$로 수렴하게 됩니다.
3그래서, 위에 보이는 것처럼, [1,0,0], [0,1,$-\delta_1$], [0,$\delta_1$,1] 이런 형식의 매트릭스를 얻게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4 (11).jpg){% endraw %}|

마찬가지로, $z$축에 대해서 $\delta_2$ 만큼의 회전을, 역시 $\delta_2$가 굉장히 작다고 했을 경우
결과적으로, [1,$-\delta_2$, 0], [$\delta_2$, 1, 0], [0,0,1]이라 하는 이러한 매트릭스를 얻게 됩니다.
이랬을 경우에는, $R_1$ 과 $R_2$를 곱했을 때 이 결과값이 $\delta_2$와 $\delta_1$을 곱했을 때, 즉 어떤 식으로 먼저 로테이션을 수행하는지 $x$축으로 먼저 돌리고 나중에 $y$축을 돌리고, $y$축을 먼저 돌리고, $x$축을 나중에 돌리고 이런 굉장히 작은 로테이션일 경우에는 로테이션도 마치 $x$방향, $y$방향, $y$방향, $x$방향, 이런 식으로 Translation, 즉 이동하는 것과 마찬가지로 commute하다는 것을 확인할 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4 (12).jpg){% endraw %}|

Rodrigues'formula를 통해서, 이것들이 어떻게 증명이 되는지 한변 살펴보도록 하겠습니다.
Rodrigues'formula에서 이 formula를 이용해서 나온 $\delta$값이 굉장히 작다고 했을 때 위에 보이는 식처럼, $I+\delta[\lambda X]$로 이렇게, 마지막에 있는 항이, $1-cos\delta$였기 때문에 $cos\delta$가 1이었습니다. 그래서 $cos\delta$를 1로 치환하게 되면 사라지고 이와 같은 $sin\delta$가, $\delta$가 되는 이런 식으로 주어지게 되고

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4 (13).jpg){% endraw %}|

이런 식으로 주어진 것들을 바탕으로 해서 $\delta_1$만큼 $\delta_2$만큼,어떤 식으로 이루어지더라도, 결과적으로는 이와 같이, 위에 보이는 식처럼, $I+\delta_1,\delta_2$의 조합으로 표현이 된다는 것을 확인할 수 있습니다. 그래서, 굉장히 작게 돌아갔을 경우에는 작은 각도로 회전할 경우에는 로테이션끼리 서로 commute한다는 것을 확인할 수 있게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4 (14).jpg){% endraw %}|

한번 정리를 하고 넘어가자면, 우리는 로테이션을 표현하는 여러 방법이 있다고 이야기했고,
그 로테이션을 표현하는 방법은, 로테이션 매트릭스라고 얘기하기도 하고, direction cosine matrix라고 하기도 합니다.

다른 한편으로는, 어떠한 프레임에 대해서, 다른 프레임의 기준좌표, XYZ를 어떻게 표현하는지에 대한, 그 표현법이라고 말하기도 하고,

그 다른 프레임 원래의 프레임에서의 한 벡터를 이 기준좌표계의 XYZ로 투영시키기 위해서, projection시키기 위해서, projection시키는 개념으로, 로테이션 매트릭스를 살펴보기도 했습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4 (15).jpg){% endraw %}|

또는, Euler angle로서 2개의 좌표계를 바꾸는 방법 12개의 각기 다른 센서를 통해서 표현하는 방법도 살펴보았고

그리고, Euler axis와 Euler angle을 통해서 하나의 축과 회전 각도를 통해서 2개의 좌표계를 완벽하게 일치시킬 수 있다는 것도 살펴보았습니다.

이 2가지, 금방 말했던 축과 각도를 가지고 표현하는 4가지의 파라미터로 표현하는, quaternion 방법을 통해서, 각도를 표현하는 것도 가능하고 이런 것들은 Euler angle이 가지는 단점들을 어느 정도는 제거할 수 있다고 말씀드렸습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA3-4 (16).jpg){% endraw %}|

여기까지 배운, 이러한 내용을 바탕으로, 어떤 좌표에서 어떻게, 이러한 개념에서 저러한 개념으로, 그 표현하는 방법과 개념들 사이의 상관관계와, 모든 것들을 왔다갔다할 수 있는 그러한 방법들에 대해서 익숙해질 필요가 있을 것입니다.



