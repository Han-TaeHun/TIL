![image (4)](https://github.com/user-attachments/assets/559476d9-76b5-4f4f-8e35-e3a691ce9d19)


- 첫번째 풀이
    - $E(x) = e^x$
    - $g(x) = x^3$
    - $e^{x^3} = E(g(x))$
    - 이것은 chain rule
    - $\frac {df} {dx} = e^{x^3} 3x^2$
- 두번째 풀이
    - 아래의 식을 활용하여 푼다.
        - $g(x) = 2^x =e^{x ln2} = (e^{ln2})^x$
        - $\frac {dg} {dx} = e^{xln2}ln2$ $= 2^xln2$
            - 자연로그 성질을 적용함
    - x로 편미분
        - $3^{xy} = e^{ln3xy}= e^{ln3xy}ln3y -> 3^{xy}(ln3)y$
    - y로 편미분
        - $3^{xy}(ln3)x - zcos(y)$
    - z로 미분
        - -sin(y)

![image (5)](https://github.com/user-attachments/assets/eda1c5c9-68ad-4ab7-9fa2-bcbc8202496c)


![image (6)](https://github.com/user-attachments/assets/3a14e4b6-24d8-4d85-a09b-481109141f16)


- $f_n$이 표기될 때 n은 행렬의 위치이다.
- 루트가 씌어진 값을 미분하는 법
    - $\frac {d} {dx} \sqrt {x} =\frac {d} {dx} (x^{\frac {1} {2}}) = \frac {1} {2}x^{\frac {1} {2} - 1} = \frac {1} {2}x^{- \frac {1} {2}} = \frac {1} {2 \sqrt {x}}$
- 하나씩 행렬에 대입하면서 편미분값을 구해주면됨