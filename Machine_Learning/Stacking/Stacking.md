데이터 출처

[[ML] 스태킹(Stacking) 완벽 정리](https://hwi-doc.tistory.com/entry/스태킹Stacking-완벽-정리)

 **스태킹의 핵심 개념**

> **여러 가지** **모델들의 예측값을 최종 모델의 학습 데이터로 사용**
> 

> 여러 개의 예측 모델을 조합하여 최종 예측 성능을 향상시키는 방법
> 

![](https://velog.velcdn.com/images/hth623/post/e1ec4ad5-2a5d-4a6e-b69f-3053d2d30ac9/image.PNG)

### 스태킹의 기본 개념

스태킹은 두 가지 레벨(Level)로 구성됩니다:

1. **기본 학습기(Base Learners)**
    - 여러 개의 서로 다른 모델(예: 선형 회귀, 의사결정 나무, 랜덤 포레스트, 신경망 등)이 첫 번째 단계에서 학습됩니다.
    - 각 기본 학습기는 독립적으로 데이터를 학습하고 예측을 수행합니다.
2. **메타 학습기(Meta Learner)**
    - 기본 학습기들의 예측 결과를 입력으로 받아 최종 예측을 수행하는 모델입니다.
    - 메타 학습기는 보통 간단한 모델(예: 선형 회귀)을 사용하며, 기본 학습기의 예측값을 특징(feature)으로 사용하여 학습합니다.

### 스태킹의 과정

![](https://velog.velcdn.com/images/hth623/post/04790784-1dff-481b-a07a-0f81fbb5630a/image.png)

출처 - https://www.google.com/url?sa=i&url=https://m.blog.naver.com/fbfbf1/222497098747&psig=AOvVaw0vw1ISXUtwtcW0lmy8JjMN&ust=1722154203669000&source=images&cd=vfe&opi=89978449&ved=0CBEQjRxqFwoTCOjS473ixocDFQAAAAAdAAAAABAE

1. **훈련 데이터 분할**
    - 원래의 훈련 데이터를 두 개의 서브셋으로 분할합니다: 하나는 기본 학습기를 훈련시키기 위한 서브셋이고, 다른 하나는 메타 학습기를 훈련시키기 위한 서브셋입니다.
2. **기본 학습기 훈련**
    - 각 기본 학습기는 첫 번째 서브셋을 사용하여 학습됩니다.
    - 훈련된 기본 학습기는 두 번째 서브셋에 대해 예측을 수행합니다.
3. **메타 학습기 훈련 데이터 생성**
    - 기본 학습기가 두 번째 서브셋에 대해 예측한 결과를 수집하여 메타 학습기의 훈련 데이터를 생성합니다. 이 훈련 데이터의 각 샘플은 기본 학습기의 예측값으로 이루어져 있습니다.
4. **메타 학습기 훈련**
    - 메타 학습기는 기본 학습기의 예측값을 입력으로 받아 학습됩니다.
5. **최종 예측**
    - 새로운 데이터가 들어오면, 기본 학습기가 이 데이터에 대해 예측을 수행하고, 이 예측값들이 메타 학습기에 입력되어 최종 예측을 도출합니다.

### 장점

- **성능 향상**: 여러 모델의 장점을 결합하여 일반적으로 단일 모델보다 성능이 더 우수합니다.
- **유연성**: 서로 다른 알고리즘을 조합할 수 있어 다양한 문제에 적용 가능합니다.

### 단점

- **복잡성**: 모델이 많아질수록 계산 비용이 증가하고, 이해 및 유지보수가 어려울 수 있습니다.
- **오버피팅**: 잘못 구성된 스태킹 모델은 오히려 성능이 떨어질 수 있습니다.

1단계 예시코드

```python
from sklearn.model_selection import KFold

# 훈련, 테스트 데이터 결과를 담을 변수 준비
oof_train = np.zeros((len(train), 1))
oof_test = np.zeros((len(test), 1))

fold = KFold(n_splits=3, random_state=42)

for trn_idx, val_idx in fold.split(train):
    x_tr, y_tr = train[trn_idx], target[trn_idx]
    x_val, y_val = train[val_idx], target[val_idx]
    model.fit(x_tr, y_tr)
    
    #검증 데이터 예측, val_idx로 선택하여 1/3 Fold 데이터만 변수에 저장
    oof_train[val_idx] = model.predict(x_val)
    
    # 학습된 모델로 테스트 데이터도 예측 수행
    # 3으로 나누느 이유는 3번 예측을 수행하기 때문에 평균을 내기 위함
    oof_test += model.predict(test) / 3
```

2단계 예시 코드

```python
# 모델 4개를 사용했다고 가정했을 때 다음과 같이 4개의 결과를 합쳐서
# 하나의 2단계 입력 값을 만든다.
train_2nd_input = np.concatenate(
(oof_train_model1, oof_train_model2, oof_train_model3, oof_train_model4), axi=1
)

test_2nd_input = np.concatenate(
(oof_test_model1, oof_test_model2, oof_test_model3, oof_test_model4), axi=1
)

# 2단계 예측 결과를 담을 변수를 만든다.
oof_train_2nd = np.zeros((len(train_2nd_input),1))
oof_test_2nd = np.zeros((len(tet_2nd_input),1))

for trn_idx, val_idx in fold.split(train):
    x_tr, y_tr = train_2nd_input[trn_idx], target[trn_idx]
    x_val, y_val = train_2nd_input[val_idx], target[val_idx]
    model.fit(x_tr, y_tr)
    
    # 마찬가지로 예측을 수행하고 결과를 저장
    oof_train_2nd[val_idx] = model.predict(x_val)
    test_2nd_input += model.predict(test_2nd_input) / 3
```

### 스태킹의 성능을 올리는 방법

- 모델에 들어가는 피처를 다르게 하여 다양성을 추가한다.
- 같은 모델이더라도 파라미터를 다르게 한다.
- 다양한 모델을 추가
- 2단계 모델의 입력에는 1단계 모델의 예측 값뿐만 아니라 원본 피처의 일부를 추가할 수 있다.
- 2단계 모델을 다양하게 시도해보고 여러 모델의 결과를 다시 스태킹하거나 평균 값을 취할 수 있다.