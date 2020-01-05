---
title: "Robot Manipulator and Underwater Robot Application 2주차 2-5 특이값 변환"
strapline: "About Robotics"
description: "RMaURA K-MOOC 강좌 정리"
header:
 overlay_image: /assets/images/triangular.jpeg
categories:
  - "Robotics"
tag:
  - "K-MOOC"
toc: true
last_modified_at: 2019-04-01 
comments: true
mathjax: true
classes: wide
---

## 특이값 분해(Singular Value Decomposition, SVD)

### 고유벡터와 고유값

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-5.jpg){% endraw %}|

선형 변환의 개념일 때, 어떠한 벡터를 집어넣었는데, 그 벡터의 차원이 바뀌지 않고, 방향도 그대로 유지하면서, 크기만 바뀌는, 특수한 어떤 방향이 존재하게 됩니다. 이러한 특수한 방향이 존재하고, 그 특수한 방향에 대해서 얼마만큼의 배율로 늘어나거나 줄어드는지를 설명하는 것이, 고유값과 고유벡터라고 말합니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-5 (2).jpg){% endraw %}|
|*특수한 벡터 K와 연결되어서, 특수한 벡터 K를 곱했을 때, 그 K를 그쪽 방향으로는 람다만큼 증가시키는, 0이 아닌 람다만큼 증가시키는 효과를 나타내는 것을 고유값이라고 한다.*|

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-5 (3).jpg){% endraw %}|

$\lambda$를, 이 $(A-\lambda I)$라는 매트릭스를, singular 값이 되게 하는 $\lambda$를 찾아서, 그 $\lambda$ 값을 통해서, 하나씩 하나씩 대입함으로서, $K$값을 구할 수 있게 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-5 (4).jpg){% endraw %}|

이렇게 구해진 고유값과 고유벡터에서, 어떤 경우에는 고유값은 항상 존재하지만, 고유값에 대한 고유벡터가 존재하지 않는 경우도 생깁니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-5 (5).jpg){% endraw %}|

Singular Value Decomposition에서는, 만약에 어떤 매트릭스 $A$가 주어졌을 떄, 그 $A$는 $A=U \Sigma V^T$라는 식처럼, $U$와 $\Sigma$와, $V$라는 3개의 매트릭스로 항상 분해가 가능합니다.

앞에서 설명했던 이 Range space와 Null space의 개념처럼, Range space의 크기를 갖는, $A$의 Row space, Null space의 개념들을 활용해서, $U$라고 하는, 서로 orthogonal basis를 가진 이런 매트릭스와 만약에 A라는 매트릭스가 아래로 긴 행렬이라면 아래로 대각선이 일정 부분까지만 연결되는, 대각선으로 된 항목들은 값을 갖지만, 나머지는 0이 되는 $\Sigma$ 매트릭스, 그리고 역시 orthogonal basis를 갖고 있고, $A$의 row space를 구성할 수 있는 각각의 벡터들로 이루어진 이 $V$라는 매트릭스, 이렇게 $U$,$\Sigma$,$V$라는 3개의 매트릭스로, $A$를 분해할 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-5 (6).jpg){% endraw %}|

먼저 일단 각각의 $U$는 Column space $A$에 의해서 $U$를 먼저 Coulmn에, 이 $A$의 Rank만큼 Coulmn space를 결정하고, 그 나머지 공간들은 이 앞에서 구해진 column space의 수직하도록 맞추어 구성하면 됩니다. 임의로 구성해주되, 앞의 column space와 직교하는 항들로만 구성해서, 전체 basis를 구성하면 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-5 (7).jpg){% endraw %}|

마찬가지로, $V$도 $A$의 Row space만큼을 구성하고, 나머지는 이 앞에 있는 Row space, $A$의 Row space에 직교되는 공간으로 채워주면 됩니다. 그래서 특징들은 orthogonal basis를, 전체를 채울 수 있도록만 만들어주면 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-5 (8).jpg){% endraw %}|

앞서서, $A$라고 하는 선형변환, 매트릭스는 선형변환의 하나의 개념으로 설명할 수 있다고 했는데요.

만약에 2개의 차원이 똑같은 2차원이라고 생각해본다면, 위 그림처럼, 원으로 구성되어 있는 전체 요소, 즉 각각의 X방향과 Y방향의 크기가 1로 전체 구성되어있는, 크기가 1인 공간을, $A$라는 매트릭스를 거치게 되면, 새로운 공간으로 어떻게 변화되는가 하면, 옆으로 이렇게 타원형을 형성하면서 좀 돌아간, 즉 축이 바뀌고, 그 축에 대한 길이의 비율이 바뀌는 이러한 변환으로 $A$라는 매트릭스를 설명할 수 있습니다.

그렇다면, 주어진 원이라는 공간이 $A$라는 매트릭스를 통해서 변환되는 과정을, Singular Value Decomposition $A$를 통해서 다시 설명하자면, 먼저 앞에서 Singular Value Decomposition, 즉 $A=U \Sigma V^T$라고 했을 때, 결과적으로는 $V^T$가 먼저 변환에 활용됩니다.

그렇다면, 어떤, 이 원이라는 공간을, $V^T$로서, 변환을 시킨다면, 이 $V^T$는 일종의 회전 매트릭스입니다.

어떤 방향으로 회전하게 되냐면, 이 변환을, $A$라는 매트릭스를 통해서 변환하게 되면, $A$를 회전시키고, 특수한 방향으로 찌그러뜨리는 그러한 역할을 한다고 말했는데요, 즉 어떤 방향으로 증폭시키고, 어떤 방향으로는 조금 축소시키는, 그러한 방식으로 변환이 이루어지는데 즉 $V^T$를 통해서, 이 공간, 주어진 공간을 회전시키고, 회전시키는 것은 찌그러뜨리기 좋은, 어떤 프레스에 집어넣어 빵을 찍어내듯이, 찍기 좋은 방향으로 돌려주고, $\Sigma$ 매트릭스만큼, 어떤 방향으로 늘리고, 어떤 방향으로는 찌그러뜨리는 역할을 $\Sigma$ 매트릭스가 한다. $\Sigma_1$과 $\Sigma_2$에 의해서, 그 비율만큼, 타원형의 형태로 바뀌게 되는 것입니다.

원래 우리가 바라보는 관점에서 어떻게 돌아갔는지 다시 돌려놓기 위해서 $U$라는 매트릭스를 통해서 다시 돌려주는 역할,
즉 $A$라는 변환은 언제 돌려주고, 눌러주고, 다시 돌려서 원래대로 복구시키는 과정의 일환으로서 이루어지는 것을 Singular Value Decomposition, 즉 SVD를 통해서 물리적인 설명이 가능합니다.

이렇게 이루어진 것을 SVD의 그래픽컬한 설명이라고 말할 수 있습니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-5 (9).jpg){% endraw %}|

그렇다면, 이러한 Singular Value Decomposition을 어떻게 구할 수 있느냐, 어떻게 정의할 수 있느냐 하는 것은, $A^TA$를 취하게 되면, $A^T$ 같은 경우는 아까 앞서서 트렌스포즈, 여러 개의 매트릭스들이 곱해져 있을 경우에 트렌스포즈를 취하게 되면 순서를 바꾼다고 했습니다. 그래서 위에 보이는 식처럼, $V \Sigma^T U \Sigma V^T$의 형태로 쓰여집니다.
여기에서, $U^TU$는 이 자체가 orthogonal basis로 구성되어 이루어져 있기 때문에 이 $U^TU$는, Identity matrix이다.
그래서 실용적으로는 $V \Sigma^2$은 m by m 매트릭스의 형태로 구성되면서 $V \Sigma^2 V^T$가 됩니다.

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-5 (10).jpg){% endraw %}|

$V$라는 매트릭스를 구해내기 위해서는 $A^TA$라는 이렇게 연산을 취하는 것들 이렇게 취해진 매트릭스의 고유값을 그리고 고유벡터를 구하는 방법으로 바로 $V$를 정의할 수 있게 됩니다.

이와 마찬가지로 $AA^T$를 하게 되면 동일하게, $U \Sigma^2 U^T$ 형태를 얻게 됩니다. 역시 마찬가지로, $AA^T$를 새로운 매트릭스로 치환하면 $U$는 그 새로운 매트릭스의 eigenvector가 되기 때문에, 이렇게 구해진 eigenvector로서 $U$를 구성하게 되면, SVD에서 $U$를 찾을 수 있게 됩니다.

마지막으로, $\Sigma^2$ 같은 경우에는 이 $\Sigma^2$은, $A^TA$와 $AA^T$에서 모두 나오게 되는데 차원이 조금 다릅니다. 다르지만 결국에는 전체가 가지고 있는 $A$가 가지고 있는 Range, 즉 전체의 Rank 숫자만큼 0이 아닌 원소로 채워질 것이기 때문에, 그 원소만 빼게 되면, $\Sigma$도 손쉽게 eigenvalue를 통해서 구할 수 있게 됩니다. 밑의 식처럼, $\sigma_i(A)= \sqrt{ \lambda(A^TA)}$   식처럼 마지막으로 $\Sigma$ 매트릭스를 구해낼 수 있게 됩니다

|{% raw %}![alt](/assets/images/K-MOOC/RMaURA/K-MOOC_RMaURA2-5 (11).jpg){% endraw %}|

그렇다면 Singular Value Decomposition을 어디에서 사용하는가 하면 앞서서 이 선형변환의 역변환으로 설명했던  Pseudo-inverse를 설명했었는데 이 Pseudo-inverse에서, $A^+$를 구할 때 그 Pseudo-inverse를 Moore-Penrose pseudo-inverse의 경우에는 $JJ^T$, $AA^T$ 같은 식으로 썼는데 그보다 좀 더 편리한 방법으로 만약에 $A$라는 매트릭스를, Singular Value Decomposition을 할 수 있다면 $A^+= V \Sigma^+ U^T$ 형태로 쓸 수 있습니다. $V$와 $U$는 앞의 식을 그대로 사용하면 되고,

$\Sigma^+$는 앞에서 pseudo-inverse를 구할 때 말했던 것처럼 $(\Sigma \Sigma^T)^-1$ 이런 식으로 해야 하지만 그럴 필요 없이 pseudo-inverse를 구할 때, $\Sigma$의 경우에는 대각선의 성분만 남아있기 때문에 대각선의 성분에 역수를 취해주면 아래로 긴 행렬이면 옆으로 긴 행렬로 옆으로 긴 행렬이면 아래로 긴 행렬로 정방행렬이면 그대로 즉 각각의 대각선 요소들만 역수를 취해주게 되면, 바로 $\Sigma$의 pseudo-inverse를 구할 수 있게 됩니다. 이러한 방식으로 Singular Value Decomposition을 활용해서 Pseudo-inverse를 구하는 데에도 사용이 가능하다고 말할 수 있습니다.







