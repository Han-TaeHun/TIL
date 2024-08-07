https://lightgbm.readthedocs.io/en/stable/

LightGBM (Light Gradient Boosting Machine)은 Gradient Boosting Framework 중 하나로, Microsoft에서 개발되었습니다. LightGBM은 대규모 데이터셋에서 빠르고 효율적으로 학습할 수 있도록 설계되었으며, 특히 메모리 사용을 줄이고 학습 속도를 높이기 위해 다양한 최적화 기법을 포함하고 있습니다. 다음은 LightGBM의 주요 특징과 장단점입니다. LGBM(Light GBM)은 **leaf-wise 트리 확장 구조**로 변경하여 속도와 메모리를 비약적으로 향상시켰다. Light GBM은 다른 알고리즘이 트리를 수평으로 확장하는 것에 반해 **트리를 수직으로 확장**한다.  

![1-s2 0-S0958946521003620-gr5](https://github.com/user-attachments/assets/4266d9a5-8f33-451e-abbd-2f690bb257a6)

### 주요 특징

1. **Leaf-wise Tree Growth (리프 중심 트리 성장)**:
    - LightGBM은 트리를 성장시킬 때 깊이 우선 방식이 아닌 리프 중심 방식을 사용합니다. 즉, 리프 노드 중 손실 감소가 가장 큰 리프를 계속해서 분할합니다.
    - 이는 같은 손실 감소를 얻기 위해 필요한 노드 수를 줄이고, 모델을 보다 효율적으로 만듭니다.
2. **Histogram-based Decision Tree Algorithm**:
    - 연속형 데이터를 분할할 때, 데이터 값을 여러 개의 구간(bin)으로 나누어 히스토그램을 생성한 후, 각 bin을 기준으로 분할점을 선택합니다.
    - 이를 통해 메모리 사용량을 줄이고 계산 속도를 높일 수 있습니다.
3. **Support for Categorical Features**:
    - 범주형 변수를 원-핫 인코딩 없이 직접 처리할 수 있는 기능을 제공합니다.
4. **Gradient-based One-Side Sampling (GOSS)**:
    - 데이터셋의 크기가 매우 클 경우, 손실에 큰 영향을 미치는 데이터 포인트를 더 많이 샘플링하여 사용합니다. 이는 계산 비용을 줄이는 데 기여합니다.
5. **Exclusive Feature Bundling (EFB)**:
    - 상호 배타적인 특성들을 묶어(번들링) 다차원 문제를 단순화하여 메모리 사용을 줄입니다.

### 장점

1. **빠른 학습 속도 및 낮은 메모리 사용**:
    - Leaf-wise 성장 전략과 히스토그램 기반 방법으로 인해 XGBoost 등 다른 Gradient Boosting 알고리즘보다 빠르고 메모리 효율적입니다.
2. **높은 정확도**:
    - 대규모 데이터셋에서도 우수한 성능을 발휘하며, 복잡한 데이터 패턴을 잘 학습합니다.
3. **대규모 데이터 처리**:
    - 대규모 데이터셋에서도 효율적으로 동작하며, 데이터셋의 크기에 비례하여 성능이 잘 확장됩니다.
4. **범주형 데이터 지원**:
    - 범주형 변수를 직접 처리할 수 있어 사전 데이터 변환 과정이 줄어듭니다.
5. **병렬 학습**:
    - 병렬 처리를 지원하여 학습 속도를 더욱 높일 수 있습니다.

### 단점

1. **과적합 가능성**:
    - Leaf-wise 트리 성장 전략은 복잡한 모델을 생성하기 쉬워 과적합(overfitting)의 위험이 있습니다. 이로 인해 정규화와 같은 추가적인 조정이 필요할 수 있습니다. 보통 1만개 이상의 행을 가진 데이터에 사용하는 것을 추천
2. **복잡한 하이퍼파라미터 튜닝**:
    - 최적의 성능을 얻기 위해서는 여러 하이퍼파라미터를 세심하게 조정해야 할 필요가 있습니다.
3. **모델 해석의 어려움**:
    - 앙상블 학습의 특성상, 모델이 복잡해지면 해석이 어렵습니다. 이를 보완하기 위해 SHAP 값과 같은 해석 도구를 사용할 수 있습니다.

### 코드 예시

다음은 `scikit-learn`과 호환되는 LightGBM의 사용 예시입니다.

```python
python코드 복사
import lightgbm as lgb
from sklearn.datasets import load_boston
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error

# 데이터 로드 및 분할
boston = load_boston()
X_train, X_test, y_train, y_test = train_test_split(boston.data, boston.target, test_size=0.2, random_state=42)

# 데이터셋 생성
train_data = lgb.Dataset(X_train, label=y_train)

# 모델 파라미터 설정
params = {
    'objective': 'regression',
    'boosting_type': 'gbdt',
    'metric': 'mse',
    'num_leaves': 31,
    'learning_rate': 0.05,
    'feature_fraction': 0.9
}

# 모델 학습
model = lgb.train(params, train_data, num_boost_round=100)

# 예측 및 평가
y_pred = model.predict(X_test, num_iteration=model.best_iteration)
mse = mean_squared_error(y_test, y_pred)
print(f"Mean Squared Error: {mse}")

```

LightGBM은 다양한 데이터 과학과 머신러닝 문제에 효과적으로 사용될 수 있으며, 특히 대규모 데이터셋과 빠른 학습이 요구되는 경우에 유용합니다.