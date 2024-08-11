![image (7)](https://github.com/user-attachments/assets/5ced0158-b07b-4659-a481-1e55ddac9961)


- $C = \sum_i (a_i^{(L)} - y)^2$
    - $C$ 는 스칼라, 비용함수
    - $y$는 정답으로 준 값
    - $a_i$ 모형을 거쳐서 나온 출력값
    - $a_i^{(L)} = \sigma(z_i^{(L)})$은 활성화 함수를 거쳐서 나온 값
    - $z_i^{(L)} = W_i^{(L)}a_i^{(L-1)}+b_i^{(L)}$
    - $W$ 와 $b$를 찾는 것
        - W와 b는 벡터
    - $W$와 $b$를 미분 $C$의 최소화하는 지점을 찾자
    - 미분을 chain rule을 이용해서 함 바로  $C$로 갈 수 없기에
    - $\frac {\partial C} {\partial W} = \frac {\partial C} {\partial a} \frac {\partial a} {\partial z} \frac {\partial z} {\partial W}$
    - $\frac {\partial C} {\partial b} = \frac {\partial C} {\partial a} \frac {\partial a} {\partial z} \frac {\partial z} {\partial b}$
- 최소값 C를 찾기 위해서 아래 과정을 계속해서 반복
    - $\sigma (W\sigma (Wa+b) + b)$