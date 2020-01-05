---
title: "Robot Manipulator and Underwater Robot Application 5주차 5-3 Algebraic approach"
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

## Algebraic approach

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3.jpg){% endraw %}|

Algebraic solution에서는 기하학적인 방법에 의존하는 것이 아니라 각각의 값들을 해석적으로 수학적인 식들만 가지고 풀이하는 방법을 의미합니다.
수식을 좀 간단하게 표현하기 위해서 $\cos(\theta_1)$은 줄여서 $c_1$, $\cos(\theta_1+\theta_2)$는 $c_{12}$라는 notation을 사용해서 활용을 하도록 하겠습니다.
그러면 앞서서 설명드렸던 $X$점, $Y$점, 그리고 각도를 표시하는 $\theta$는 각각 이렇게 위에서처럼 $l_1c_1 + l_2c_{12}$, $l_1s_1+l_2s_{12}$ 이렇게 표현이 가능하겠죠.
이렇게 표현한 상태에서 이렇게 $X$점하고 $Y$점이 주어졌을 때 이 안에 들어가있는 수식들은 전부다 $\sin$과 $\cos$의 값을 포함하고 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (2).jpg){% endraw %}|

$\sin$하고 $\cos$을 활용을 해서 어떤 수식을 풀어나갈 때 가장 좋은 방법중의 하나는 바로 제곱을 통해서 $\cos^2 + \sin^2 = 1 $이라는 성질을 활용하는 것입니다.
조금전에 보여드렸던 수식에서 $x$와 $y$를 제곱해서 더하게 되면
바로 이와 같이 $l_1^2 c_1^2 + l_2^2 c_{12}^2 + 2l_1l_2 c_1 c_{12}$ 이런 한 묶음, 즉 $x$에 대한 제곱과 $y$에 대한 제곱으로 이 두가지 식을 더할 수가 있겠됩니다.
이렇게 더해주게되면 여기에서 아까 말씀드렸던 것 처럼 $\cos^2$과 $\sin^2$ 같은 경우에는 더하게 되면 1이되죠, 그래서 두 식이 더해져서 $l_1^2$만 남게되구요,
역시 마찬가지로 l2제곱에 c12의제곱을 전부다 더하게 되면, 마찬가지로 c12의제곱과 s12의제곱을 더함으로써 l2의 제곱만 남게됩니다.
결과적으로는 $l_1^2+ l_2^2 + 2l_1l_2(c_1 c_{12} + s_1 s_{12})$라는 이렇게 제곱이 되지 않는 항들만 남게되는 것 입니다.
여기서 $\cos$과 $\sin$의 덧셈법칙을 활용하게 되면 $\cos a \cos b + \sin a \sin b$ 형태이기 때문에 이 두개를 더하면 \cos의 뺼셈법칙이 적용되서 결과적으로는 $2l_1l_2c_2$만 남게됩니다.
이렇게 주어지게 되면 앞서 마찬가지로 $(1)^2 + (2)^2$이라고 되어 있는 부분은 각각 $x$하고 $y$구요, $x$하고 $y$는 주어진 값 끝점에 위치했으면 좋겠다라고 하는 그 값이 되겠고 $l_1 l_2$ 역시 주어진 값이 되겠습니다. 
결과적으로는 모르는 값은 $c_2$만 되겠고, 그래서 $c_2$를 arc \co\sine을 이용하면 이와 같이 주어지게 되는데
조금전에 Geometric solution에서 발견했던 그 식과 정확하게 일치하는 수식이 됩니다.

결과적으로는 해석적 접근법은 그림에 의존하는 것이 아니라, 단지 $\cos$과 $\sin$의 제곱, 그리고 그 관계식을 활용한 것 뿐인데 같은 결과를 얻을 수 있다는 것을 확인할 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (3).jpg){% endraw %}|

2자유도 manipulator 에서 한걸음 더 나아가서 똑 같은 평면이지만 3자유도 manipulator 에 대해서는 어떻게 해석할 수 있는지 한번 살펴보도록 하겠습니다.
이번에는 3자유도이고, 그리고 마지막 manipulator 의 각도, End-effector의 각도를 의미하는 $\phi$값까지 총 세개, $x$,$y$, $\phi$값을 내가 이렇게 움직였으면 좋겠다, 이 manipulator가 이렇게 움직였으면 좋겠다라고 하는 방식으로 입력을 넣어주게 됩니다. Geometric 한게아니라 algebraic하게 풀이합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (4).jpg){% endraw %}|

그렇다면 역시 $x$ $y$ $\phi$가 주어지구요, $\theta_1$, $\theta_2$, $\theta_3$를 구하기 위해서 $x$ $y$ $\phi$에 대한 수식을 위에서 보이는 식들과 같이 정리할 수가 있는데요.
이 중에서 $\phi$라고 하는 값은 $\theta_1 + \theta_2 + \theta_3$로 주어지게 되고, $\phi$는 갔으면 좋겠다고 하는 주어진 기본값입니다.
그렇기 때문에 알고 있는 값이라서 위에 있는 $x$ $y$의 각각 맨 마지막 항인 $l_3c_{123}$ , $l_3s_{123}$의 코싸인과 싸인값은 기본값이라고 생각해도 무방합니다.
즉 $\phi$값이 주어짐으로써 $\theta_1 + \theta_2 + \theta_3$의 최종적인 합은 얼마다라는 것을 알 수 있기 때문입니다. 그렇다면 앞서와 마찬가지로  $l_3c_{123}$ , $l_3s_{123}$를 알고 있는 값이 앞쪽으로 빼보게되면 우리는 식은 두 개구요, 모르는 미지수는 구하고자 하는 $\theta_1$과 $\theta_2$ 두 개 이기 때문에 역시 비슷한 방법으로 구할 수 있을 것입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (5).jpg){% endraw %}|

그러면 역시 앞서와 마찬가지로 이 두식을 한번 제곱을 해서 더해보도록 하겠습니다. 그러면 알고있는 값으로 $x$를 다시한번 바꿔서 정의를 해보겠습니다.
주어진 $x$, 가고자하는 $x' = x – l_3c{_\phi}$ 전부다 아는 값들이죠.
이 아는 값들로 구성된 $x'$과 마찬가지로 $y – l_3s{_\phi}$ 를 포함하는 $y'$. 그래서 $x'$과 $y'$으로 다시한번 식을 정리하면
위에보이는 식 처럼, $x' – l_1c_1 = l_2c_{12}$ 이렇게 하나의 식과, $y' – l_1s_1 = l_2s_{12}$ 이렇게 두 개의 식으로 식을 다시한번 정리해볼 수 있겠구요. 역시 여기에서도 양변을 한번 제곱해보도록 하겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (6).jpg){% endraw %}|

양변을 제곱을 해서 더해주게 되면, 이와 같은 식으로 주어지게 되겠구요.
이렇게 주어지는 이유는 앞서 말씀드린 것 처럼 각각의 $\sin^2$과 $\cos^2$을 가지고 있는 그러한 성분들은 전부다 더해서 1이되기 때문이죠. 이렇게 최종적으로 식이 주어지게 되는데요.
이렇게되면 이 안에 식을 들여다보면 $l_1x'$ , $l_1y'$ , $x'$ , $y'$ , $l_1$, $l_2$는 전부 아는 값이죠. 오로지 모르는 값은 $\theta_1$만 모르게 되겠죠.
그렇다면 식은 하나로 주어지구요, 구해야 되는 값이 $\theta_1$으로 결정이 되기 때문에 이 식은 풀 수가 있는데, 식이 좀 복잡하죠.
하나는 $\cos(\theta_1)$ $\sin(\theta_1)$ 서로 선형적이지 않은 이러한 식들이 들어가있기 때문에, 이런 식을 풀기 위해서 새로운 방법을 한번 도입해 보도록 하겠습니다.

$\theta_1$과 하나의 식이 주어져 있는데, $\sin$만 들어가 있거나 $\cos$만 들어가 있을 경우에는 보통은 $\arcsin$, $\arccos$이라는 함수를 이용해서 구하면 쉽게 구할 수 있는데요.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (7).jpg){% endraw %}|

이와 같이 싸인과 $\cos$이 동시에 들어가 있을 경우에는, 하나의 새로운 변수를 정의를 해서 그 변수를 통해서 새롭게 식을 만들어 줄 수 가 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (8).jpg){% endraw %}|

먼저, 앞서서 있는 식을 이렇게 다시한번 써보도록 하겠습니다. $P \cos \alpha + Q \sin \alpha + R = 0$ 이런식으로 식을 다시 이렇게 다시 쓴 상태에서 $\gamma$라는 각도를 새롭게 정의를 할 텐데요.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (9).jpg){% endraw %}|

바로 이 $\gamma$라는 각도는 $Q \above 1pt \sqrt {P^2 + Q^2}$와 그다음에 $P \above 1pt \sqrt {P^2 + Q^2}$라는 두 개의 값을, $arctan$으로 하는 $\gamma$를 정의하게 되겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (10).jpg){% endraw %}|

이렇게 정의를 해서 다시 조금전에 새롭게 정의한 식에다가 대입을 하게 되면, ${\cos\gamma \cos\alpha + \sin\gamma \sin\alpha} + {R} \above 1pt \sqrt {P^2 + Q^2}$ 의 형태로 식을 이렇게 쓸 수가 있습니다.

여기서 보시면 여러분들 좀 낯익은 수식이 보여요. $\cos\gamma \cos\alpha + \sin\gamma \sin\alpha$ 바로 코싸인의 뺄셈법칙을 활용 할 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (11).jpg){% endraw %}|

그래서 $\cos(\alpha - \gamma)$는 결과적으로 $-R \above 1pt \sqrt {P^2 + Q^2}$이 됩니다.

그러면 이렇게 주어지게 되면 $\sin$이 없어지고 $\cos$만 남게되기 때문에 역시 $\arccos$이라는 걸 이용해서 $\alpha = \gamma + \sigma \arccos(-{R} \above 1pt \sqrt {P^2 + Q^2})$이 되겠습니다.
여기서 $\sigma$는 옆에 보이시는 것처럼 $\pm 1$이라고 말씀을 드렸는데요.
앞서서 Algebraic solution에서 그리고 또 Geometric solution에서 살펴봤던 것 처럼 $\cos$ 같은 경우에는 $\arccos$의 경우에 +,- 두 개의 값을 복수의 솔루션으로 갖는다고 말씀을 드렸습니다.
그래서 그 값을 표시하기 위해서 이렇게 $\pm 1$이라는 값을 $\sigma$에 대입을 하게 되면 이렇게 두 개의 솔루션을 다 포함하게 되는 그런 식을 얻을 수가 있게됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (12).jpg){% endraw %}|

원래 식에서 $-2l_1x'$을$P$라고 정의를 했었고, 그리고 $-2l_1y'$을 $Q$ 그리고 나머지 뒤에 있는 식들을 $R$이라고 표시 했습니다. 이렇게 $P$, $Q$, $R$을 활용해서 $\gamma$를 정의 하겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (13).jpg){% endraw %}|

$\gamma$를 정의해보면 즉, 위에 있는 수식으로 $\arccos$값을 정의할 수가 있습니다

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (14).jpg){% endraw %}|

결과적으로 이렇게 $\gamma$값을 앞서서 정의를 했었고, 그리고 조금전처럼 $\arccos$에 들어가는 인자들은 모두 찾을 수가 있었습니다. 앞서서 구했던 그러한 방법들을 통해서 $\theta_1$을 정의할 수가 있습니다.
이렇게 구한 $\theta_1$을 이제는 앞에서 사용했었던 $x - l_3c\phi = l_1c_1 + l_2c_{12}$ 라는 $x$에 대한 식과 그리고 마찬가지로 $y$에 대한 식에다가 각각 $\theta_1$의 값을 집어넣도록 하겠습니다.
각각의 값을 집어넣게 되면 남는 식들은 결과적으로는 $\theta_2$에 대한 식만 주어지게 됩니다.
그래서 $\theta_2$에 대한 식, $\theta_1$,$\theta_2$에 대한 식이죠 엄밀히 말하면, $\theta_1$,$\theta_2$에 대한 식이 주어지면 그 $\theta_1$,$\theta_2$에 대한 식을 이용해서 $arctan$라는 명령어를 활용을 해서 $\theta_1$,$\theta_2$를 구하게 되고,
$\theta_1$,$\theta_2$에서  $\theta_1$을 빼주게되면 최종적으로 $\theta_2$를 구할 수 있게 되는 것이죠. 이렇게 해서 $\theta_2$를 구했구요, 다시 $\theta_2$을 앞서서 구했기 때문에

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (15).jpg){% endraw %}|

$\theta_1$과 $\theta_2$를 모두 구한 상태에서 우리는 이 식들을 활용을 해서 $\phi – (\theta_1 + \theta_2)$라는 값을 활용을 하게 된다면 이 식들을 통해서 $\theta_3$는 쉽게 결정을 할 수가 있겠죠.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (16).jpg){% endraw %}|

앞서 살펴본 것 처럼, $\theta_1$,$\theta_2$,$\theta_3$를 순차적으로 하나씩 Algebraic solution을 이용해서 구할 수가 있었고요. 앞서서 $\theta_1$을 구했을 때 $\sigma$는 $\pm 1$이 된다
즉 두 개의 솔루션을 얻을 수 있다. 그래서 이 두 개의 식을 어떻게 그림으로 표현을 할 수가 있냐하면 위에 보이시는 것 처럼 $\sigma = -1$이라면 lower arm, 즉 암의 형태가 아랫쪽으로 이렇게 구부러지는 형태가 되는 이러한 형상을 띄게되는 것이고 반대로 $\sigma = +1$ 이라는 값을 나타내면 upper arm 이렇게 위로 구부러지는 형태의 복수개의 솔루션을 얻게됩니다.

이랬을 때 $theta_1$과 $\theta_2$는 각각의 값들에 따라서 부호가 같이 결정되는 그러한 형태가 됩니다.
$\theta_3$같은 경우 복수로 얻어지지 않는 이유는 $\theta_1$과 $\theta_2$가 결정이 되면 결국에는 마지막 $\phi$값을 결정해주기 위해서,
즉, 마지막 End Effector가 사용하는 각도를 결정해 주기 위해서 마지막 축은 항상 같은 위치를 차지하고 있어야 하기 때문에 $\theta_3$에 대해서는 단일 솔루션을 얻게 되는 것 입니다.
여기에서 만약에 구해야 하는 점이 있는데, 그 점이 범위를 벗어난다거나 또는 $\theta_1$, $\theta_2$, $\theta_3$를 결정할 수 없거나,
그 솔루션을 찾을 수 없을 경우에, 우리는 그 지점을 \singular point라고 이야기 합니다.
\singular point라고 하는 것은 즉, 가고싶은 $x$, $y$, $\phi$가 있을 때 그 $x$ $y$ $\phi$에 해당하는 $\theta$값을 정할 수 없는 경우를 \singular point, 즉 특이점이라고 이야기 하고 이 특이점에 대해서는 보다 자세하게는 나중에 속도기구학을 설명할 때 조금 더 자세하게 설명 드리도록 하겠습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA5-3 (17).jpg){% endraw %}|

그리고 조금전에 3자유도 manipulator에 대해서 평면상에서의 3자유도 모션, 즉, $x$,$y$ $\phi$가 전부 주어졌을 때 1:1로 $\theta$값들을 결정을 해 봤습니다.
그것이 결정되지 않았을 경우를 \singular point라고 얘기했습니다.
만약에 끝점의 위치는 중요하지만 끝점의 각도는 중요하지 않을 경우, 즉 "끝점의 각도는 상관없으니까 니맘대로해, 나는 $x$,$y$만 잘 쫓아갔으면 좋겠어" 라고 사용자가 입력을 넣어주게 된다면 $\phi$값에 대해서는 값이 없기 때문에, 어찌보면 이 끝점의 위치를 고정하고 많은 자세들을 만들 수 있습니다.

즉, orientation이 specify 되지 않은 orientation을 특정하지 않았을 경우에는 무한히 많은 솔루션들, 나중에 이것을 null motion 이라고 얘기할 건데요.
Redundant manipulator의 개념에서 잠시 다시한번 자세하게 설명을 드릴텐데 무한대의 솔루션, 즉 이런 무한대의 솔루션이 나오는 경우는 일반적으로 관절공간에서의 자유도 공간이 작업공간의 자유도 보다 많을 경우
작업공간은 원래는 $x$,$y$,$\phi$였는데 $\phi$는 관여하지 않는다고 얘기 했기 때문에, $x$,$y$ 2차원으로 표현이 되고
관절공간은 $q_1$, $q_2$, $q_3$ $\theta_1$, $\theta_2$, $\theta_3$ 처럼 세 개의 자유도로 구성이 되어 있기 때문에 관절자유도가 작업공간자유도보다 높아서 발생하는 현상 입니다.
이럴경우를 Redundant case라고 얘기하고, 이 케이스에 대해서는 역시 속도기구학에서 조금 더 자세히 설명 드리도록 하겠습니다.





