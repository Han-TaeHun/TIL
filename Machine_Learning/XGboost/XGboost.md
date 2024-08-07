XGBoost(eXtreme Gradient Boosting)는 Gradient Boosting 알고리즘을 기반으로 한 머신러닝 라이브러리입니다. 뛰어난 성능과 효율성으로 인해 다양한 데이터 과학 및 머신러닝 대회에서 자주 사용됩니다. 주요 특징과 개념은 다음과 같습니다 .**XGboost의 핵심 아이디어는 각 피처 데이터들을 일정 간격으로 나눠 최적의 분기점을 찾는다는 것이다**. 여러개의 Decision Tree를 조합해서 사용하는 Ensemble 알고리즘

![선택 영역_192](https://github.com/user-attachments/assets/e8c23ea2-7b3f-4dae-9cb3-c145c90a4d74)

### 주요 개념

1. **Gradient Boosting**:
    - Gradient Boosting은 여러 개의 약한 학습자(보통 결정 트리)를 결합하여 강력한 예측 모델을 만드는 앙상블 학습 방법입니다.
    - 모델은 반복적으로 학습하여 이전 모델의 예측 오차를 줄이는 방식으로 학습을 진행합니다.
2. **XGBoost의 특징**:
    - **Regularization (정규화)**: 모델의 복잡도를 제어하여 과적합(overfitting)을 방지합니다.
    - **분산 학습**: 병렬 처리 및 분산 학습이 가능하여 대규모 데이터셋에서도 빠르게 학습할 수 있습니다.
    - **Sparsity Awareness**: 희소 데이터(많은 값이 0인 데이터)를 효율적으로 처리합니다.
    - **Custom Objective Functions**: 사용자가 직접 손실 함수를 정의할 수 있습니다.
    - **Early Stopping**: 검증 세트의 성능이 향상되지 않을 때 학습을 조기 종료하여 과적합을 방지합니다.
    - **병렬 처리와 GPU 지원:**  XGBoost는 병렬 처리를 지원하므로 대용량 데이터셋에서도 빠른 학습과 예측이 가능합니다. 또한, GPU를 활용하여 계산 속도를 향상시킬 수 있습니다.

### 작동 원리

1. **모델 초기화**:
    - 초기에는 모든 예측값이 0이거나 평균값으로 초기화됩니다.
2. **순차적 학습**:
    - 각 단계에서 새로운 약한 학습자(결정 트리)를 추가하여 이전 학습자의 예측 오차를 보정합니다.
    - 새로운 학습자는 오차에 대한 그래디언트(기울기)를 계산하고 이를 최소화하는 방향으로 학습합니다.
3. **가중치 업데이트**:
    - 각 약한 학습자가 예측한 결과에 대한 가중치를 업데이트합니다. 이 과정은 목표 함수(손실 함수)를 최소화하는 방향으로 진행됩니다.
4. **최종 모델 생성**:
    - 여러 학습자의 가중치 합으로 최종 예측을 수행합니다.

### 주요 하이퍼파라미터

1. **n_estimators**: 생성할 결정 트리의 수.
2. **max_depth**: 트리의 최대 깊이로, 과적합을 방지하기 위해 사용됩니다.
3. **learning_rate**: 각 트리의 가중치 크기를 줄이는 파라미터로, 낮출수록 학습이 느리지만 과적합을 방지할 수 있습니다.
4. **subsample**: 트리를 학습할 때 사용할 데이터의 비율로, 과적합을 방지할 수 있습니다.
5. **colsample_bytree**: 트리를 학습할 때 사용할 특성의 비율.

![선택 영역_191](https://github.com/user-attachments/assets/52092e9a-0d81-4954-9631-45d51546cd90)

### 코드 예시

다음은 `scikit-learn`과 호환되는 XGBoost의 사용 예시입니다.

```python
python코드 복사
import xgboost as xgb
from sklearn.datasets import load_boston
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error

# 데이터 로드 및 분할
boston = load_boston()
X_train, X_test, y_train, y_test = train_test_split(boston.data, boston.target, test_size=0.2, random_state=42)

# 모델 학습
model = xgb.XGBRegressor(n_estimators=100, max_depth=3, learning_rate=0.1)
model.fit(X_train, y_train)

# 예측 및 평가
y_pred = model.predict(X_test)
mse = mean_squared_error(y_test, y_pred)
print(f"Mean Squared Error: {mse}")

```

XGBoost는 그 효율성과 성능 덕분에 다양한 실제 응용 프로그램에 널리 사용되며, 특히 대규모 데이터셋을 다룰 때 유용합니다.