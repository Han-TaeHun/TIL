![image](https://github.com/user-attachments/assets/ab4913b0-76c7-4fbf-b675-0a174bbede3a)

- 라그랑주 승수법?
    - 여러 개의 제약 조건을 가진 최적화 문제를 해결하는 수학적 기법입니다.
    - 주로 미적분학이나 최적화 이론에서 사용되며, 제약 조건하에서 함수의 극대값이나 극소값을 찾는 데 유용
- 라그랑주 승수법의 기본 개념
    1. **목표 함수**: 최적화하려는 함수로, 일반적으로 최대화 또는 최소화하려는 대상입니다. 예를 들어, $f(x, y$)가 있을 수 있습니다.
    2. **제약 조건**: 목표 함수에 추가되는 조건으로, 등식 형태로 주어집니다. 예를 들어, $g(x, y) = 0$ 같은 형태입니다.
    3. **라그랑주 함수**: 목표 함수와 제약 조건을 결합하여 새로운 함수를 정의합니다. 이 함수는 다음과 같이 정의됩니다
        
        $$
        ⁍
        $$
        
        여기서 $\lambda$는 라그랑주 승수로, 제약 조건의 중요도를 나타내는 변수입니다.
        
    4. **편미분**: 라그랑주 함수를 각 변수 $x, y, \lambda$에 대해 편미분하여 각 변수에 대한 도함수를 구합니다.
        
        $$
        ⁍
        $$
        
- **라그랑주 승수법**에서 **람다(λ)제약 조건이 목적 함수의 최적값에 미치는 영향력**을 나타내는 **상수**
- 예제
    
    목표 함수 $f(x, y) = x^2 + y^2$를 최소화하고, 제약 조건 $g(x, y) = x + y - 1 = 0$을 고려한다고 가정해 보겠습니다.
    
    1. 라그랑주 함수:
        
        $$
        \mathcal{L}(x, y, \lambda) = x^2 + y^2 - \lambda (x + y - 1)
        $$
        
    2. 편미분:
        
        $$
        \frac{\partial \mathcal{L}}{\partial x} = 2x - \lambda = 0
        $$
        
        $$
        \frac{\partial \mathcal{L}}{\partial y} = 2y - \lambda = 0
        $$
        
        $$
        \frac{\partial \mathcal{L}}{\partial \lambda} = -(x + y - 1) = 0
        $$
        
    3. 방정식 풀이:
        
        $$
        x = \lambda, \quad 2y = \lambda, \quad x + y = 1
        $$
        
        $$
        x = y, \quad 2x + 2y = 2, \quad x + y = 1
        $$
        
        $$
        x = y = \frac{1}{2}
        $$
        
        따라서, $(x, y) = \left(\frac{1}{2}, \frac{1}{2}\right)$에서 최소값을 갖습니다.
        
- 오른쪽에 $≤ 0$ 이라는 조건을 정의해줘야 $\sum_i \lambda_i g_i (x)$이 식을 바로 가져올 수 있음
- 이걸로 구한 지역 최솟값이 곧 전역 최솟값이 될 수 있기 때문에 아주 좋음 파워풀하다
- $x^2 + y^2$의 제약조건( $x + y -1$ )을 만족하는 최솟값을 구하는 예시
    - 제약조건과 $x^2 + y^2$ 의 기울기가 깔끔하게 상쇄된 상태
    - 아래 그림처럼 원과 직선 그래프의 접점의 기울기의 상수배를 확인 하는것 이 $L(x, \lambda) = f(x) + \sum_i \lambda_i g_i(x)$ 식이다.
    
    ![image (1)](https://github.com/user-attachments/assets/9fdace6f-1f9d-4d38-8e20-7f27c75d641d)
    

![image (2)](https://github.com/user-attachments/assets/ef0fbf8d-ff4a-4031-b56e-84a669539c79)

- $L(x, \lambda) = x^2 +\lambda(x_1 + x_2 -1)$
- $\nabla L_x = 2x +\lambda[:] = 0$
- $\nabla L_\lambda =x_1 + x_2 -1 = 0$

### 문제 설정

- **목표 함수**:
    
    $f(x) = x_1^2 + x_2^2 + \cdots + x_n^2$
    
- **제약 조건**:
    
    $g(x) = x_1 + x_2 - 1 = 0$
    

### 2. 라그랑주 함수 작성

라그랑주 함수를 다음과 같이 정의합니다:

$$
⁍
$$

즉,

$$
\mathcal{L}(x, \lambda) = x_1^2 + x_2^2 + \cdots + x_n^2 - \lambda (x_1 + x_2 - 1)
$$

### 3. 편미분 방정식 세우기

라그랑주 함수를 각 변수 $xi (i = 1, 2, ..., n)$와 $\lambda$에 대해 편미분합니다.

$$
\frac{\partial \mathcal{L}}{\partial x_1} = 2x_1 - \lambda = 0
$$

$$
\frac{\partial \mathcal{L}}{\partial x_2} = 2x_2 - \lambda = 0
$$

$$
\frac{\partial \mathcal{L}}{\partial x_i} = 2x_i = 0 \quad \text{for } i = 3, 4, \ldots, n
$$

$$
\frac{\partial \mathcal{L}}{\partial \lambda} = -(x_1 + x_2 - 1) = 0
$$

### 4. 방정식 풀이

위의 방정식들을 풀어봅시다.

1. $2x_1 = \lambda$ 이고, $2x_2=λ$ 이므로, $x_1=x_2$입니다.
2. $2x_i = 0$이므로, $x_i=0 (i=3,4,…,n)$입니다.
3. $x_1 + x_2 = 1$이고, $x_1=x_2$이므로, $2x_1=1$이 됩니다. 따라서, $x_1=x_2=\frac{1}{2}$입니다.

### 5. 결과

따라서, 최적해는 다음과 같습니다.

$$
⁍
$$

여기서 x의 각 원소를 제곱하여 합한 결과, 즉 $f(x)$는 $\left(\frac{1}{2}\right)^2 + \left(\frac{1}{2}\right)^2 = \frac{1}{4} + \frac{1}{4} = \frac{1}{2}$입니다. 이 값이 최소값입니다.

![image (3)](https://github.com/user-attachments/assets/15dce773-4924-4d15-a35e-0b98d2553c27)

- KKT 조건이란?
    - 라그랑주 승수법을 일반화한 형태로, 비등식 제약 조건과 등식 제약 조건이 모두 포함된 문제를 다룰 수 있습니다.

![image (4)](https://github.com/user-attachments/assets/8e847adf-953d-4df0-a2ec-b27af74751e2)

- KKT 조건의 구성 요소
    - **Stationarity:** 목적 함수의 그래디언트와 제약 조건들의 그래디언트의 선형 결합이 0이 되어야 합니다.
    - **Primal Feasibility:** 모든 제약 조건을 만족해야 합니다.
    - **Dual Feasibility:** 모든 라그랑주 승수는 음이 아닌 실수여야 합니다.
    - **Complementary Slackness:** 각 제약 조건에 대응하는 라그랑주 승수와 그 제약 조건의 함수값의 곱이 0이 되어야 합니다.

![image (5)](https://github.com/user-attachments/assets/835e429e-b8d6-444e-a77d-8f256074b0be)

- 

### 라그랑주 함수 정의

라그랑주 함수를 정의합니다:

$$
\mathcal{L}(x, y, \lambda, \mu) = f(x, y) + \lambda g_1(x, y) + \mu h(x, y)
$$

$$
\mathcal{L}(x, y, \lambda, \mu) = x^2 + y^2 + \lambda (x^2 + y^2 - 5) + \mu (x + 2y - 4)
$$

### 2. KKT 조건 설정

**(a) Stationarity (정지 조건)**:

라그랑주 함수 $\mathcal{L}(x, y, \lambda, \mu)$를 $x, y, \lambda, \mu$에 대해 편미분하고 0으로 설정합니다.

$$
\frac{\partial \mathcal{L}}{\partial x} = 2x + 2\lambda x + \mu = 0 \quad (1)
$$

$$
\frac{\partial \mathcal{L}}{\partial y} = 2y + 2\lambda y + 2\mu = 0 \quad (2)
$$

$$
\frac{\partial \mathcal{L}}{\partial \lambda} = x^2 + y^2 - 5 \leq 0 \quad (3)
$$

$$
\frac{\partial \mathcal{L}}{\partial \mu} = x + 2y - 4 = 0 \quad (4)
$$

**(b) Primal Feasibility (1차 조건 만족)**:

$$
x^2 + y^2 \leq 5, \quad x + 2y = 4, \quad x \geq 0, \; y \geq 0
$$

**(c) Dual Feasibility (2차 조건 만족)**:

$$
\lambda \geq 0
$$

**(d) Complementary Slackness (보충 여유 조건)**:

$$
\lambda (x^2 + y^2 - 5) = 0 \quad (5)
$$

### 3. 방정식 풀기

**(4)에서**:

$$
x + 2y = 4 \quad \Rightarrow \quad y = 2 - \frac{x}{2}
$$

이를 (1)과 (2)에 대입합니다.

**(1)에서**:

$$
2x(1 + \lambda) + \mu = 0 \quad \Rightarrow \quad \mu = -2x(1 + \lambda) \quad (6)
$$

**(2)에서**:

$$
2y(1 + \lambda) + 2\mu = 0 \quad \Rightarrow \quad y(1 + \lambda) + \mu = 0 \quad (7)
$$

(6)을 (7)에 대입합니다.

$$
y(1 + \lambda) - 2x(1 + \lambda) = 0
$$

$y = 2 - \frac{x}{2}$를 대입하면:

$$
(2 - \frac{x}{2})(1 + \lambda) - 2x(1 + \lambda) = 0
$$

이 식을 풀어봅니다. $\lambda = 0$인 경우와 $\lambda > 0$인 경우로 나누어 풀 수 있습니다.

**(i)  $\lambda = 0:$**

$\mu = -2x$

$$
x + 2(2 - \frac{x}{2}) = 4 \quad \Rightarrow \quad x + 4 - x = 4 \quad \Rightarrow \quad x = 0
$$

$$
y = 2 - \frac{0}{2} = 2
$$

**(ii) $\lambda > 0$:**

$x^2 + y^2 = 5x2+y2=5, x+2y=4$를 동시에 만족해야 합니다.

$$
⁍
$$

이 방정식을 풀어보면:

$$
x = 2, \quad y = 1
$$

### 4. 최적해

$x = 2, y = 1$일 때:

$$
f(x, y) = x^2 + y^2 = 2^2 + 1^2 = 5
$$

$\lambda = 0$일 때는 $f(x, y) = 0 + 4 = 4$가 최소값입니다.

따라서 최적해는 $x = 0, y = 2$이며, 이 때 최소값은 4입니다.