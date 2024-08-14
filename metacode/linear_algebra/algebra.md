# Point

- “.” = [0, 1] = 존재하거나 존재하지 않거나

# Scalar = $\mathbb{R}$

- 1 차원 데이터
- 수 자체를 의미
- 하나의 수 체계 안에 속함
    - $1, 2, 3,4,5\in \mathbb {Z}$
- 세상의 모든 데이터들이 수직선(1개) 위에 있다.

![image](https://github.com/user-attachments/assets/14fb050a-1a3f-4456-a261-ba1f7630ea02)
# Vector = $\mathbb{R} ^n$

- 2차원 데이터 (차원이 늘어날 수 있음)
    - `z` 3개를 묶어서 표현할 수 있기 때문
    - $[1, 2] \in  \mathbb {R} ^2$
    - $[1, 2, 3] \in  \mathbb {R} ^3$
    - $[n개] \in  \mathbb {R} ^n$
- 수직선이 2개 ( `X정보`, `Y정보`를 가지고 있음)
- scalar가 연달아 붙어있는 것 (수학적으로는 의미가 살짝 다르지만 일단 이렇게 이해)
- Scalar들의 모음

![image (1)](https://github.com/user-attachments/assets/9055a6eb-b8bf-4cc0-beb1-7620c3d124fa)

# Matrix = $\mathbb{R} ^{n*m}$

- 2차원 벡터 (벡터가 또 나열된 것)
    - 예시
        
        $\begin{bmatrix}
        a & b \\
        c & d \\
        e & f
        \end{bmatrix} \in \mathbb{R}^{3*2}$
        
    - 
- Vector들이 쌓인 것

# 고려할 부분

`행` 또는 `열`이 1개이면 이것은  `Vector`이다

$$
a \in \mathbb{R}^{n * 1} = vector
$$

# Tensor = $\mathbb{R} ^{n*m*k}$

- Matrix가 쌓인 것
- 예시
    - 가로 360 세로 480 그리고 RGB 3개의 채널을 가지고 있는 이미지는
    - $image \in \mathbb{R}^{360*480*3}$

![image (2)](https://github.com/user-attachments/assets/6f0be911-9349-4cf9-88f1-7757188a0b86)