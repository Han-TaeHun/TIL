![Untitled](https://github.com/user-attachments/assets/d794ac13-2a0d-4482-8abe-653da4ea05c2)

- $\lim_{\epsilon \to 0} \frac {f(x_A +\epsilon) - f(x_A)} {\epsilon}$

### 앱실론의 의미

- **아주 작은 양:** 앱실론은 보통 임의의 아주 작은 양을 나타낼 때 사용됩니다.
- **오차의 허용 범위:** 어떤 값이 특정 값에 '충분히 가깝다'는 것을 표현할 때, 그 '충분히'라는 개념을 수량화하기 위해 앱실론을 활용합니다.

![Untitled (1)](https://github.com/user-attachments/assets/387cedbe-0a6d-4446-b0bd-5d4967a33724)

- $\lim_{x \to k}c = c$
    - 상수일 때는 그대로 사용한다.
- $\lim_{x \to k}x = k$
    - x가 k로 가까워지면 그냥 k
- 더하기 할 때 분해가능
- 곱셉도 분해가능

![Untitled (5)](https://github.com/user-attachments/assets/d2eb4f76-c586-439a-b045-ee3c39982890)


- $x_A$가 아니라 그냥 $x$
- 미분은 함수의 도함수를 구하는 과정입니다.

예를 들어, $f(x) = x^2$인 경우:
- **도함수**: $f′(x)=2x$
    
- **미분값**: $x=2$에서의 미분값은 $f′(2)=4$
- 미분을 한다는 것은 먼저 도함수를 구하고, 이후에 그 도함수를 사용하여 특정한 $x$에서의 미분값을 계산할 수 있음을 의미
  

![Untitled (3)](https://github.com/user-attachments/assets/3fa88f53-13f2-49a1-9162-245628341aec)

- 상수 c의 경우는 일직선이므로 미분값이 0
- 각각의 함수가 합으로 연결되어있으면 각각의 도함수로 연결한다.
- 곱셉이라면 각각의 도함수를 취하지 않는 경우를 곱해준다.
- 분수는… 빡세다 외우라고 하심…
- 제곱일 때는 $px^{p-1}$ 이다 꿀 공식
    - $f(x) = \frac {1} {x} = x^{-1}$
    - $f’(x) = \frac {-1} {x^2}$
- **여기부터는 암기…………..**
- $f(x) = exp(x) → f’(x) = exp(x)$
- $f(x) = ln(x) → f’(x) = \frac {1} {x}$
- $f(x) = sin(x) → f’(x) = cos(x)$
- $f(x) = cos(x) → f’(x) = -sin(x)$
- $f(x) = tan(x) → f’(x) = \frac {1} {cos^2(x)}$
- chain Rule: $f(x) = g(h(x)) → f’(x) = g’(h(x))h’(x)$
    - $g(h(x))$ 일단 $g$부터 미분하고 나중에 안에 있는 것만 빼서 미분 후 곱해준다.

![Untitled](https://github.com/user-attachments/assets/9357c18e-f589-4b1b-b7e1-a373dded8466)

- 미분의 기본 포맷
    - $\lim_{\epsilon \to 0} \frac {f(x + \epsilon) - f(x)} {\epsilon}$
- 상수(c)일 때는 위 형태에서 분자가 $c-c$가 되기 때문에 그냥 0
- 덧셈
    - $\lim_{\epsilon \to 0} \frac {g(x + \epsilon) + h(x + \epsilon) - g(x) - h(x)} {\epsilon}$
    - $\lim_{\epsilon \to 0} \frac {g(x + \epsilon) - g(x) +  h(x + \epsilon) - h(x)} {\epsilon}$
    - $\lim_{\epsilon \to 0} \frac {g(x + \epsilon) - g(x)} {\epsilon}$ + $\lim_{\epsilon \to 0} \frac {h(x + \epsilon) - h(x)} {\epsilon}$
    - $g’(x) + h’(x)$
- 곱셈
    - $\lim_{\epsilon \to 0} \frac {g(x + \epsilon)h(x + \epsilon) - g(x)h(x)} {\epsilon}$
    - $\lim_{\epsilon \to 0} \frac {g(x + \epsilon)h(x + \epsilon) + g(x)h(x + \epsilon) -g(x)h(x + \epsilon) - g(x)h(x)} {\epsilon}$ 여기서 $g(x)h(x + \epsilon)$를 추가
    - $\lim_{\epsilon \to 0} \frac {g(x + \epsilon) - g(x) } {\epsilon} h(x)$ + $\lim_{\epsilon \to 0} \frac {h(x + \epsilon) - h(x) } {\epsilon} g(x)$
    - $g’(x)h(x) + h’(x)g(x)$
- chain rule
    - $f(x) =  g(h(x))$
    - $\lim_{\epsilon \to 0} \frac {g(h(x + \epsilon)) - g(h(x))} {\epsilon}$
    - $\lim_{\epsilon \to 0} \frac {h(x + \epsilon) - h(x)} {h(x + \epsilon) - h(x)}$ *  $\lim_{\epsilon \to 0} \frac {g(h(x + \epsilon)) - g(f(x))} {\epsilon}$
    - $h’(x) * \lim_{\epsilon \to 0} \frac {g(h(x + \epsilon)) - g(h(x))} {h(x + \epsilon) - h(x)}$
        - $u = h(x + \epsilon)$
        - $v = h(x)$
    - $h’(x) * \lim_{u \to v} \frac {g(u) - g(v)} {u -  v}$
    - $h’(x) g’(h(x))$
    

![Untitled (1)](https://github.com/user-attachments/assets/b442ff39-0487-4603-a52a-c69857713ff1)

- $f’(x) = 3x^2 + cos(x)$
- 코사인이 함수를 감싸고 있다. → chain rule
    - $-sin(3x^2)$
    - $- 6x sin(3x^2)$