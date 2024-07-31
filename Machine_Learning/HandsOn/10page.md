# 10.1 생물학적 뉴런에서 인공 뉴런까지

### 10.1.2 뉴런을 사용한 논리 연산

이미지출처 -https://excelsior-cjh.tistory.com/172

- 매컬러와 피츠가 생물학적 뉴런에서 착안한 매우 단순한 신경망 모델을 제안했는데, 이것이 나중에 `인공 뉴런`이 되었다.
- 이 모델은 하나 이상의 이진(`on/off`) 입력과 하나의 이진 출력은 가진다.
- 단순히 입력이 일정 개수만큼 활성화되었을 때 출력을 내보낸다.

![image](https://github.com/user-attachments/assets/535969aa-0233-4b54-80d8-326436aa783f)

- 왼쪽 첫 번째 네트워크는 `항등 함수`입니다. `뉴런 A`가 활성화되면 `뉴런 C`도 활성화됩니다.
- 두번째 네트워크는 논리곱 연산을 수행한다. `뉴런 A와 B`가 모두 활성화 될 때만 `뉴런 C`가 활성화된다.
- 세 번째 네트워크는 논리합 연산을 수행한다. `뉴런 A와 B` 중 하나가 활성화되면 `뉴런 C`가 활성화 된다.
- `뉴런 A`가 활성화되고 `뉴런 B`가 비활성화될 때 `뉴런 C`가 활성화 된다.

### 10.1.3 퍼셉트론

- 퍼셉트론은 가장 간단한 인공 신경망 구조
- `TLU` 또는 `LTU`라고 불리는 조금 다른 형태의 인공 뉴런을 기반으로 한다.

![image](https://github.com/user-attachments/assets/e268e882-1125-400a-a5a3-ac34df302607)

- `TLU`는 간단한 선형 이진 분류 문제에 사용될 수 있다.
- `TLU`를 훈련한다는 것은 최적의 $w_1, w_2, b$를 찾는다는 뜻이다.
  
![image](https://github.com/user-attachments/assets/f7adcbb0-be1a-4965-b8d6-32893d32380e)

$$
h_{W,b}(X) = \phi(XW + b)
$$

- $X$는 입력 특성의 행렬, 이 행렬의 행은 샘플, 열은 특성이다.
- 가중치 행렬 W는 모든 연결 가중치를 포함한다.(행렬이라서)  이 행렬의 행은 입력에 대항하고 열은 출력 층에 있는 뉴런에 해당한다.
- 편향 벡터 $b$는 뉴런마다 하나씩 모든 편향을 포함
- $\phi$를 활성화 함수라고 부른다.
- “서로 활성화되는 세포가 서로 연결된다.” 즉, 두 뉴런이 동일한 출력을 낼 때마다 이 둘 사이의 연결 가중치가 증가

$$
w_{i,j}^{(next step)} = w_{i,j} + \eta(y_i - \hat{y}_j)x_i
$$

- $w_{i,j}$:  $i$ 번째 입력 뉴런과 $j$번째 출력 뉴런 사이를 연결하는 가중치
- $x_i$: 현재 학습 데이터 샘플의 $i$ 번째 뉴런의 입력값
- $\hat{y}_j$ : 현재 학습 데이터 샘플의 $j$ 번째 출력 뉴런의 출력값
- $y_i$: 현재 학습 데이터 샘플의 $i$번째 출력 뉴런의 실제값
- $\eta$ : 학습률

사이킷 런으로 Perceptron을 구현한 예

```python
import numpy as np
from sklearn.datasets import load_iris
from sklearn.linear_model import Perceptron

iris = load_iris(as_frame=True)
X = iris.data[["petal length (cm)", "petal width (cm)"]].values
y = (iris.target == 0)

per_clf = Perceptron(random_state=42)
per_clf.fit(X, y)

X_new = [[2, 0.5], [3, 1]]
y_pred = per_clf.predict(X_new)
```

- 퍼셉트로은 간단한 문제를 풀 수 없다.  (XOR분류문제, 로지스틱회귀…)
- 다층 퍼셉트론은 위 문제를 해결할 수 있었다. ‘

### 10.1.4 다층 퍼셈트론과 역전파