![Untitled (6)](https://github.com/user-attachments/assets/31824a04-c610-4e2c-b90e-a31066ab7cb3)

미분이 정의 되지 않는 경우가 있구나

딥러닝의 대부분은 미분을 사용하여 최적화한다. 

그래서 미분이 가능한지 안하지를 알아야함

![Untitled (7)](https://github.com/user-attachments/assets/424962d4-2b1d-415e-9da4-9e3da1053598)

- $f(x) = \frac {1} {x}$ 이렇게 되면 gradient가 폭발하거나 정의가 안됨
- $x_B$는 $x_A$에 무한히 가까워질 때, $f(x_B)$도 $f(x_A)$에 무한히 가까워져야한다.
    - 이것이 연속적이라는 의미인데  `한 선에 같이 있어야한다`는 의미로 이해하자
    - 연속적이지 못하다면 미분이 가능하게 혹은 연속적이게 만들어줘야한다.
- 뾰족점 V형태의 그래프가 되면 안된다.
    - $X = x_A$에서 좌 미분계수와 우 미분계수가 같아야한다.
    - V 그래프는 좌우가 각각 1과 -1을 가짐
    - $f(x) = | x|$ 형태의 그래프가 위 사항의 예시
- tangent line = 접선
- $f(x)$는  $X = x_A$에서의 접선이 수직이면 안된다.
    - $f(x) = x^{\frac {1} {3}}$의 그래프 형태가 위 사항의 예시이다.
- 의도적으로 미분이 불가능하게 하여 학습을 더 좋게 하기도 한다.
    - 예를들면, 활성화 함수 - ReLu 형태가 미분 불가능
    - weight가 커지고 많아지는 것을 방지하기 위함