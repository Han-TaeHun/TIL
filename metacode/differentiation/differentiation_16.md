![image](https://github.com/user-attachments/assets/e71f459b-f2e4-4e41-84c7-02683a6c2521)
- Backtracking Line Search:일단 많이 가서 조금씩 줄이는 방식

- $f(X + \eta d)$
    - 현재 상태에서 가로축의 위치
- $f(x) + a \Delta f(x)^T(\eta d)$
    - 다음 스텝으로 간 위치

![image (1)](https://github.com/user-attachments/assets/c4bb018a-39da-4da3-aaec-67d8eaad8031)

![image (2)](https://github.com/user-attachments/assets/745bfcc7-c5e1-4c2e-a4a0-5c33c23961c9)

![image (3)](https://github.com/user-attachments/assets/a8209f66-801d-4fd0-99d9-89672e022ecb)

![image (4)](https://github.com/user-attachments/assets/e400df19-39e4-40ad-a694-6632f80f767a)

- Wolfe 조건은 최적화 알고리즘에서 적절한 스텝 크기를 선택하여 알고리즘의 수렴성과 효율성을 높이기 위해 사용됩니다. 이를 통해 목적 함수의 값이 충분히 감소하고, 그래디언트가 적절하게 감소하도록 보장할 수 있습니다.

- Sufficient Decrease Condition
    - Sufficient Decrease Condition은 최적화 알고리즘에서 스텝 크기를 선택할 때 사용되는 기준으로, 목적 함수의 값이 충분히 감소하는지 확인하는 역할을 합니다. 이를 통해 알고리즘의 안정성과 효율성을 높일 수 있습니다.
    - 스텝을 진행했을 때 목적 함수 값의 감소가 충분한지를 확인하기 위한 조건
    
    - f는 목적 함수입니다.
    - $x_k$는 현재 위치입니다.
    - $\alpha_k$는 스텝 크기입니다.
    - $d_k$는 검색 방향(search direction)입니다 (보통 **음의 그래디언트 방향**).
    - $\nabla f(x_k)$는 $f$의 그래디언트입니다.
    - $c_1$은 작은 양수입니다 (보통 0<c1<1).
    - $f(xk+α_kd_k)$는 현재 위치 $x_k$에서 검색 방향 $d_k$로 스텝 크기 $\alpha_k$만큼 이동했을 때의 목적 함수 값입니다
    - **충분한 감소**: 이 조건은 스텝을 진행했을 때, 함수의 값이 충분히 감소하는지 확인합니다. 단순히 함수값이 감소하기만 하는 것이 아니라, 감소량이 $c_1 \alpha_k \nabla f(x_k)^T d_k$보다 작아야 합니다.
    - **효율성 보장**: 목적 함수의 값이 너무 조금만 감소하거나, 오히려 증가하는 것을 방지하여 알고리즘의 효율성을 보장합니다.
- Curvature condition
    - 스텝 크기 선택 시 그래디언트의 감소를 보장하며, 알고리즘의 수렴 속도를 적절하게 유지하는 데 중요한 역할을 합니다. 이를 통해 최적화 알고리즘이 목적 함수의 최솟값을 효과적으로 찾아나갈 수 있도록 돕습니다.
    - 스텝 후에 그래디언트의 크기가 충분히 감소하는지 확인하기 위한 조건

- **Sufficient Decrease Condition**은 목적 함수의 값 자체가 충분히 감소했는지를 보장합니다. 이는 알고리즘이 잘 동작하고 있다는 초기 확인 단계라고 볼 수 있습니다.
- **Curvature Condition**은 그래디언트의 크기가 적절히 감소했는지를 보장하여, 알고리즘이 올바른 방향으로 나아가고 있음을 확인합니다. 이는 알고리즘의 안정성을 보장하는 역할을 합니다.