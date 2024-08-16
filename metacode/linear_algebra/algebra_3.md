- $A = \begin{bmatrix}
1 &  0 & -1 \\
2 & 0 & 1 \\
0 & 1 & 0
\end{bmatrix} \in \mathbb{R^{3*3}}$  각 열을 a, b, c라고 생각하자
- $a \text{a} + b\text{b}$ = 0  공식에 맞춰서
- 선형 독립한다

- $\mathbb{R}^{n*n} \mathbb{R}^{n*1} = \mathbb{R}^{n*1}$
- $\mathbb{R}^{a*b} \mathbb{R}^{c*d} = \mathbb{R}^{a*d}$
- 위와 같은 경우 양옆의 끝 자리가 결과값의 행렬이 된다.
- 그리고 가운데 차원 숫자가 같아야 한다.
- 매트릭스와 벡터가 연산하면 벡터가 나온다.

![image](https://github.com/user-attachments/assets/eb2bffd9-a169-49c0-93b6-f148600b5109)

- 원래의 수직선을 `Range space` 가 커버하지 못하는 부분을 `Null space`
- $A = \begin{bmatrix}
1 & 2 \\
2 & 4 \\
\end{bmatrix}$ = Rank 1

![image (1)](https://github.com/user-attachments/assets/c0ed643d-3f0b-48f6-af1f-ebc631e039a4)

- $A = \begin{bmatrix}
1 & 2 & -2\\
2 & 4 & 1\\
\end{bmatrix}$
    - 이런 경우 `span` 한다.
    - 가운에 열을 빼고 `Rank 2`를 유지한다.

# Linear Operator

![image (2)](https://github.com/user-attachments/assets/81d2d249-ecf5-46f7-9c15-64ddb8710538)

- 좌표공간을 비틀어서 새로운 단위를 정의한다.
- 곱하는 것을 변형된 좌표공간에서 읽히는 좌표 `(1, 1)`
    - 변형된 좌표계
- 원래 기준좌표계에서 읽히는 좌표 `(3, 3)`
    - 원래 좌표계

![image (3)](https://github.com/user-attachments/assets/0fddd85c-d6fc-41a7-ba2e-b06b32f35828)

# Matrix Multiplication, AB -BA =?

- 행렬의 경우에는 곱하는 순서가 영향을 미친다.
    - $AB \neq  BA$