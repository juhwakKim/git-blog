---
title: "Robot Manipulator and Underwater Robot Application 2주차 2-3 행렬과 벡터의 연산(2)"
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
last_modified_at: 2019-03-29 
comments: true
mathjax: true
classes: wide
---

서울과학기술대학교 김진현교수님의 K-MOOC강좌 Robot Manipulator and Underwater Robot Application을 공부하고 내용을 정리한 것 입니다.

K-MOOC 강좌 주소: 

<http://www.kmooc.kr/courses/course-v1:SEOULTECHk+SMOOC03k+2019_T3/about>

## 행렬과 벡터의 연산 - 2

### Vector Norms

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3.jpg){% endraw %}|
|*벡터의 크기나 측정 비교을 가능하게 해주는 요소이다.*|

#### Norm의 조건
> 1. 놈의 크기는 항상 0보다 크다, 0보다 크거나 같다. ($\text {x} = 0$인 경우만 등호가 성립한다.)
> 2. $\text {x}+y$의 크기는 절대 $\text {x}$와 $y$를 각각 구한 후, 그 둘을 더한 것보다 작거나 같아야 한다. (삼각부등식)
> 3. 상수 $α$을 곱했을 때, 상수만큼 늘어난다.

위 3 가지 성질을 만족하는 것을 놈으로 정의할 수 있습니다.

#### P-norm

|{% raw %}![alt](https://wikimedia.org/api/rest_v1/media/math/render/svg/9f2d83bfa397bdf021046004b9a365079cab6a22){% endraw %}|

p는 1보다 크거나 같고 딱히 자연수일 필요는 없습니다.

p-norm의 특수한 예로써, 1-norm(맨해튼 놈), 2-norm(유클리드 놈)이 있다.

그리고 전체 원소 중에서 가장 큰 값을 골라내는 것을 인피니티 놈이라고 합니다.

### 스칼라곱(Scalar Multiplication)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3 (2).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3 (3).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3 (4).jpg){% endraw %}|

### 벡터곱(Vector Product)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3 (5).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3 (6).jpg){% endraw %}|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3 (7).jpg){% endraw %}|

벡터곱 같은 경우에는 어떤 평면상에 있는 $A$라는 벡터와 $B$라는 벡터로 2개의 벡터곱을 취했을 경우에는, 2개의 벡터들의 공통된 수직방향, 즉 전체 면에 대한 수직방향으로 결과가 얻어지게 됩니다.

|{% raw %}![alt](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b0/Cross_product_vector.svg/220px-Cross_product_vector.svg.png){% endraw %}|

이 수직방향의 결과 때문에, 앞서 말씀드렸던 것처럼 내적을 취하게 되면 어떠한 벡터와 수직되는 벡터를 곱했을 때는, 0이 된다는 성질 때문에, 한마디로 $a\cdot(a$x$b)=0$은 $a$와 $b$ 모두에 수직되는 방향으로 결과가 도출된다는 것을 확인할 수 있습니다.

### 쌍선형 형식(bilinear form)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3 (8).jpg){% endraw %}|
|*어떤 매트릭스를 기준으로 앞에 벡터를 곱하고, 다시 뒤에도 벡터를 곱하는 이러한 연산을 쌍선형 형식이라고 합니다.*|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3 (9).jpg){% endraw %}|

이런 쌍선형 형식 중에서, 특수한 형태가 존재하는데, 만약에 $A$라는 매트릭스가 정방행렬이고, 앞에 $\text {x}^T$를 곱하고, 뒤에 $x$를 곱하는, 즉 앞에서 $x$하고 $y$가 같은 형태를, 쌍선형 형식의 특수한 형태라 해서, quadratic form(이차형식)이라고 합니다.

> 만약에 이 이차형식에서, 주어진 매트릭스 $A$가 존재하고, $A\text{x}$ = 0일때 모든 x에 대해서, 어떤 걸 넣더라도 0이 된다.

> 만약에 주어진 매트릭스 $S$가 반대칭행렬이라면, $x^TSx = 0$이 되는 성질을 갖고 있습니다.

> 만약에 어떤 반대칭행렬 $C$가 존재할 때, 그 $C$가 이차형식의 형태로 $x^TCx$라고 했을 때, 그게 0이 된다고 하면, $x$가 0이거나, $C$가 0인 경우인 상황을 제외하고는 존재하지 않습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3 (10).jpg){% endraw %}|

만약에 $A$라는 대칭행렬이 존재할 때, 이 $A$라는 대칭행렬이의 경우에는 이 이차형식은 $x$가 0이 아닌 경우를 제외하고는, 항상 0보다 큽니다. (이것을 positive definite라고 한다.)

그리고, 0까지 포함해서 모든 $x$의 경우에, 0보다 항상 크거나 같다면, positive semi-definite 이라고 합니다.

이 둘의 차이는 positive definite은 $x$가 0일 경우에만 결과가 0이 되고, positive semi-definite은 $x$가 0이 아니더라도 0은 될 수 있다는 차이가 있습니다.

0보다 작아서는 안되지만, 0은 될 수 있다는 라는 것을 positive semi-definite이라고 정의할 수 있습니다.

그 외의 동일하게, 0이 아닌 모든 $x$에 대해서, 항상 0보다 작은 결과가 나올 경우가 바로 negative definite입니다.

그리고, negative semi-definite은, 앞서 말씀 드렸던 positive semi-definite과 동일하게, 모든 $x$에 대해서, 0보다 작거나 같은 이러한 성질들을 가질 때, negative semi-definite이라고 얘기합니다.

경우에 따라서는, 0보다 크고, 0보다 작은 경우가 존재할 수 있는데, 이 경우에는 결정할 수 없다, 라고 해서 indefinite이라고 합니다.

어떤 이차형식을 미분했을 때, 앞뒤로 대칭되는 성질을 갖고 있기 때문에, $2x^TAx+x^TAx$라는 형태로, 이차형식이 주어지게 됩니다.

### 벡터와 행렬의 미분(Derivative of Vectors and Matrices)

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3 (11).jpg){% endraw %}|
|*벡터, 행렬에 미분이 필요한 이유는, 앞으로 연산을 진행할 때, 기구학을 구하고, 동력학을 구할 때, 속도, 가속도 등이 필요할 때, 표현하는 방법 중 하나가 주어진 매트릭스와 벡터를 미분하는 것이기 때문입니다*|

만약에 어떤 매트릭스의 함수, 즉 매트릭스로 이루어진 함수인 $u$,$v$가 존재하고, 모든 원소들이 전부 실수인 상수를 갖는 매트릭스 $A$가 존재할 때, 이 매트릭스 $A$를 미분한다고 할 때, 실수 상수를 가지고 있기 때문에, 항상 미분하면 0이 됩니다.

그리고, $u$,$v$라는 벡터의 경우, 흔히 알고 있는 미분의 성질을 그대로 따르게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3 (12).jpg){% endraw %}|

주어진 매트릭스와 벡터를 각각 스칼라값, 즉 일정한 상수 값으로 미분을 했을 때는, 그 주어진 디멘션을 그대로 가지면서, 각각의 원소들을 스칼라 값인 t로 미분하는, 이러한 성질을 갖습니다.

역시 마찬가지로 벡터에 대해서 미분을 하는 경우에도, 벡터의 한 원소인 $x_1$으로 미분했을 때, 원래의 벡터의 디멘션을 그대로 유지하면서 각각의 스칼라값으로 미분하는 특성을 갖습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3 (13).jpg){% endraw %}|

이제부터 중요하고, 주의해야 하는 법칙들이 나타나게 되는데, 만약에 옆으로 긴, 즉 트랜스포즈가 되어있는 벡터로서, 스칼라값을 미분한다면 어떨까요?

스칼라값을 벡터로 미분한다고 하면, 벡터가 옆으로 긴 것의 경우에는, 각각의 원소들을 이용해서 각각의 스칼라값을 미분하는 것으로 정의할 수 있게 됩니다.

마찬가지로, 아래로 긴 벡터의 형태를 이용해서, 어떤 스칼라값 $a$를 미분하게 되었을 때, 이를 흔히 벡터에서 ‘그레디언트’라고 표현하기도 합니다.

마찬가지로 각각의 원소로 $x_1$~$x_n$행까지, 벡터의 성분으로 미분하게 되는 효과를 갖게 됩니다.

매트릭스로 확장하게 되면, 마찬가지로 스칼라 값을 매트릭스의 원소로 미분하게 되면, 각각의 값을 갖고 미분을 한다고 이해하면, 큰 문제는 없을 겁니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3 (14).jpg){% endraw %}|

어떠한 벡터를 벡터로 미분하는 경우

$\partial v$, $\partial x$라는, 어떤 둘 다 $v$라는 벡터와 $x$라는 벡터가 존재하게 되고, $x$라는 벡터로 $v$라는 벡터를 미분한다고 한다면, $v$도 아래로 길고, $x$도 아래로 길다면, 이 두 벡터를 이용해서 미분을 할 때, 이에 대한 정의를 위한 새로운 디멘션이 필요할 것입니다.

그래서, 보편적으로, 벡터를 벡터로 미분할 경우에는 항상 미분당하는 벡터는 아래로 길게, 미분하는 벡터는 옆으로 길게 배치를 해서 이 규칙을 통해서 벡터를 미분하는 것이 일반적인 방법입니다.

규칙을 깨지 않고, 일반적인 성질들을 그대로 유지할 수 있는 방법이 이와 같은 정의를 사용하는 것입니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3 (15).jpg){% endraw %}|

좀 더 확장하게 되면, 만약에 $u^Tv$라고 하는, 이런 벡터 2개를 내적을 취하게 되면, 이것은 스칼라 값이 될 것입니다.

어떤 스칼라 값인, $α$가 될 테니까, 앞서서 정의한 것처럼, 옆으로 긴 벡터 $\partial x_1$~$\partial α$까지, 라운드 xn의 라운드 알파 형태로 결과값을 얻게 됩니다.

2개의 서로 다른 벡터가 있을 때, 앞의 것을 미분하고, 뒤의 것을 미분하는 방식을 그대로 사용하게 되면,

결국에는 결과값은 스칼라값, 이 형식을 유지해야 하기 때문에, 그럴 수 있도록 $v^Tu$에 대한 미분,

즉 원래 아까 정의한 것처럼, 어떤 벡터를 미분할 때에는 옆으로 긴 벡터에서 세로로 긴 벡터를 미분해야 하기 때문에, 

이러한 노테이션을 활용해서 $v^Tu$를 곱하게 되면, 아래와 같은 디멘션을 얻게 됩니다.

마찬가지로 뒤의 것을 미분할 경우에는, 이번에는 다행히도 $v$가 아래로 긴 벡터이기 때문에, 옆으로 긴 벡터에 아래로 긴 벡터를 미분하여 얻은 결과에 트랜스포즈를 하고, 동일한 결과값을 얻어, 두 결과를 더하는 방식으로, 이러한 규칙성을 따질 필요가 생깁니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-3 (16).jpg){% endraw %}|

더 나아가서, 만약에 이차형식이나, 쌍선형 형식이 주어지게 되면, 이 결과값은 결과적으로 $α$, 즉 상수값이 됩니다.
그렇기 때문에 옆으로 긴 벡터로 미분할 수 있게 됩니다.

각각의 요소들을 살펴보면, $u$에 대한 미분, $v$에 대한 미분은 큰 어려움 없이 수행할 수 있게 되고,

대신에, 가운데, $Q$에 대한 미분이 필요하게 되는데, 이 매트릭스에 대한 미분은 $x^T$로 미분하는 것까지는 좋은데, Q라는 것은 매트릭스입니다. 그렇기 때문에 미분을 하게 되면 3차원의 형태로 확장해야 합니다.

이런 어려움이 있기 때문에, 이런 부분들을, $v$하고 같이 연결지어서 이와 같이 $x^T$와 $Q$를 미분한 것에 $v$를 곱한 것을, 각기 $x_1$~$x_n$에 대한 것을, 벡터와 연결지어서 스칼라값과 하는 방법으로,

전체적인 연산방법을 깨지 않으면서, 쌍선형 형식까지 어떻게 미분할 수 있는지를 살펴보았습니다.















