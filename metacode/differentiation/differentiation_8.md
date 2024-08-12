![image](https://github.com/user-attachments/assets/0694c691-f38f-4f2f-9107-d992edadf048)

- 다변수 함수의 미분을 일반화한 개념으로, 벡터값 함수의 모든 편미분을 행렬 형태로 나타낸 것
- 많이 볼일이 없지만 도메인에 따라 볼 수도 있음
- $J$ 라고 표기함, 설명가능한 ai에 대한 부분에서 볼 수 있음
- 열단위로는 고정, 행단위로 보면 Gradient 벡터이다.
- 1차 도함수 행렬로 이해하자

### 예시: 2차원 함수의 Jacobian

**함수 예시**: ${f}(x, y) = \begin{bmatrix} u(x, y) \\ v(x, y) \end{bmatrix}$ 여기서

- $u(x, y) = x^2 + y$
- $v(x, y) = xy + y^2$

이 함수는 2차원 입력 $(x, y)$를 2차원 출력 $(u, v)$으로 변환합니다.

**Jacobian 행렬 구하기**:

1. **편미분 계산**:
    - $u(x, y)$에 대한 $x$와 $y$의 편미분:
        - $\frac{\partial u}{\partial x} = 2x$
        - $\frac{\partial u}{\partial y} = 1$
    - $v(x, y)$에 대한 $x$와 $y$의 편미분:
        - $\frac{\partial v}{\partial x} = y$
        - $\frac{\partial v}{\partial y} = x + 2y$
2. **Jacobian 행렬 구성**:
    
    Jacobian 행렬은 다음과 같이 구성됩니다:
    
    $$
    ⁍
    $$
    

### Jacobian의 의미

- **국소적 선형 근사**: Jacobian 행렬$J_{\mathbf{f}}$는 함수 $\mathbf{f}$가 특정 점 $(x, y)$에서 어떻게 변하는지를 나타냅니다. 예를 들어, $(x, y) = (1, 2)$일 때, Jacobian 행렬은:
    
    $$
    ⁍
    $$
    
    이 행렬은 입력 $(x, y)$가 미세하게 변할 때 출력 $(u, v)$의 변화를 선형적으로 근사합니다.
    
- **변환의 스케일링**: Jacobian 행렬의 행렬식(Determinant)은 함수가 특정 점에서 공간의 스케일을 어떻게 변형하는지 보여줍니다. 예를 들어, 위에서 구한 Jacobian 행렬의 행렬식은:
    
    $$
    ⁍
    $$
    
    이는 점 $(1, 2)$에서의 변환이 스케일을 8배로 변형한다는 것을 의미합니다.