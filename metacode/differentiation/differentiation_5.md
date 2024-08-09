![Untitled (4)](https://github.com/user-attachments/assets/8f126b78-66e1-4ef4-bdad-b9e5eb4b3bce)

- **도함수** = 미분하여 얻은 함수
- 최적화한다는 것 = 최소/최대값을 찾는 것
    - 꼭 미분을 사용하는 것은 아님
- 함수를 최적화하는 것은 함수를 미분하고 도함수값이 0이 되는 모든점을 찾아 목적함수가 최대/최소가 되는지 확인 하는 것
- 도함수값이 0이라고 해서 극대/극소값이 아닐 수 있다. 위 그래프 참고
- 안장점 - 말의 안장처럼 생긴거 코세라에서 봤던거

![Untitled (5)](https://github.com/user-attachments/assets/68e54006-2456-4043-8edd-be76938d41aa)

- 해석적 접근법 = Analytical Approach
    - 차원이 커지면 사용할 수 없음
- 수치적 방식은 반복하는 방식
- $x_{i+1} = x_i - \frac {y_idf} {dx}(x_i)$
    - $x_i$의 반대 방향으로 가는 것을 의미하는 공식
    - $y_i$가 스텝사이즈를 조절하는 상수
    - 가장 근본이 되는 공식