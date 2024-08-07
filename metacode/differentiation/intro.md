![Untitled (1)](https://github.com/user-attachments/assets/0f7a248f-c14f-4d48-b21c-92d4b3724555)


미분 = 순간 변화율

가중치 = 파라미터 = 모수

### 목적 함수란?

> 최적화 문제에서 최적의 솔루션을 찾기 위해 사용하는 함수입니다. 이 함수는 모델의 성능을 평가하는 데 사용되며, 목적함수를 최소화하거나 최대화함으로써 최적의 해를 구합니다.
> 

> 최적화 문제에서 **목적 함수(objective function)**는 기본적으로 값을 최소화하거나 최대화하는 것을 목적으로 하는 함수를 의미합니다(수요 예측 계산에서도 활용됩니다).
> 
> 
> 반대로 목적 함수를 최대화 또는 최소화 하는 인수를 구하는 문제가 **최적화 문제(optimization problem)**입니다.
> 

### 가우시안 모델?

> 가우시안 모델(Gaussian Model)은 통계학과 머신러닝에서 자주 사용되는 확률 분포 모델입니다. 가장 일반적으로 알려진 가우시안 분포는 정규 분포(Normal Distribution)로, 벨 모양의 곡선으로 나타내어집니다. 가우시안 모델은 데이터가 평균을 중심으로 대칭적으로 분포하며, 특정 표준 편차를 가지고 있다는 가정하에 데이터를 모델링합니다.
> 

최적화하는 알고리즘은 모형의 파라미터(모수)를 찾는 문제와 같다

### Gradient 설명이 빡셈 나중에 배울 때 정리

편미분으로 구성된 벡터

`근` = `파라미터`로 생각하자 아주 똑같은 것은 아님

딥러닝 시대에서 여러가지 최적화 방법 중에서 미분으로 하는 것이 거의 정답 즉, 중요하다

![Untitled (5)](https://github.com/user-attachments/assets/959af6de-e3f7-4706-904c-5e9fd22d067a)


slope = 기울기

위처럼 직선이면 쉽다. 

![Untitled (3)](https://github.com/user-attachments/assets/9cb72c86-9f1b-4bcd-a161-10f40b4d0d27)

위 이미지와 같은 경우에는 직선처럼 기울기를 구하는 것이 안된다….

![Untitled (4)](https://github.com/user-attachments/assets/53f8af91-906a-4462-bfed-3a6b77e65c37)


A와 B가 엄청 (무한) 가까워질 때 `함수 f`의 `점 A`에서의  `derivative`(미분값 혹은 미분계수 라고 한다. )