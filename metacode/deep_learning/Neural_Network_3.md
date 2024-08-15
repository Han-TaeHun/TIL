# Matrix Multiplication

![20240815203832](https://github.com/user-attachments/assets/1f3df03d-d5e6-4e4d-8022-a79f5c5af8f8)

- 행렬 곱할 때 규칙이 있음
    - (1, 3) x (3, 2) = (1, 2)
    - 앞부분의 열과 뒷부분의 행이 같아야하며
    - 결과는 앞부분의 행과 뒷부분의 열과 같은 형태로 나옴

![20240815204432](https://github.com/user-attachments/assets/c4bb86f3-ec40-4b3e-8d1d-6053d80efb6e)

![20240815204443](https://github.com/user-attachments/assets/1db3dd74-0303-4d13-866d-2694956190ea)

![20240815204845](https://github.com/user-attachments/assets/b8dd750e-9f33-473f-8bf7-dc1e7bc41e42)

- bmm을 사용하는 이유.jpg
    - 연산의 속도를 위하여 사용한다
    - 왼쪽으로 사용하게 되면 N개를 반복문을 사용해야하지만
    - 오른쪽은 연산 한번으로 결과를 만들기 때문에 속도가 더 빠르

# Linear Layer

![20240815205204](https://github.com/user-attachments/assets/35e3af6d-361a-4abb-8057-0751be7bc018)

![20240815205212](https://github.com/user-attachments/assets/13887314-f7f5-4c08-9967-146190ada46f)

![20240815205223](https://github.com/user-attachments/assets/023d6bcd-bc49-4ab3-a907-c25add843bbb)

![20240815210607](https://github.com/user-attachments/assets/511adde5-a8df-405c-a86c-4e203ef658c0)

- 선형함수는 여러번 사용하 효과가 없기 때문에 활성화 함수를 사용한다.
    - $ax + b = f(x)$
    - $f(f(x)) = a(ax + b) +b$
    - $= a^2x + ab+ b$
    - $= a’x + b’$ ($a’ = a^2, ab+b = b’$ 으로 치환해서 생각)
    - $= f(x)$와 형태가 같음

![20240815211503](https://github.com/user-attachments/assets/641c4001-ccd9-481a-8ba7-f90c56a3e749)

![20240815212228](https://github.com/user-attachments/assets/5d7d4494-b75e-4f6c-8499-148d9a4fdd7f)