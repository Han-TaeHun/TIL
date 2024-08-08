`Pipeline` 클래스는 여러 데이터 처리 단계와 모델링 단계를 순차적으로 연결하여 하나의 일관된 워크플로우를 만들 수 있게 해줍니다. 이를 통해 전처리, 변환, 모델 학습 및 예측 단계를 간단하게 구성할 수 있습니다.

### 주요 기능

- **단계 연결**: 전처리, 변환, 예측 등 여러 단계를 연결할 수 있습니다.
- **재사용성**: 동일한 파이프라인을 여러 데이터셋에 재사용할 수 있습니다.
- **하이퍼파라미터 튜닝**: 그리드 서치 및 랜덤 서치와 결합하여 파이프라인 전체의 하이퍼파라미터를 최적화할 수 있습니다.

### 사용 예시

```python
python코드 복사
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression

# 각 단계를 ('name', transform/estimator) 형식으로 전달
pipeline = Pipeline([
    ('scaler', StandardScaler()),  # 스케일링 단계
    ('classifier', LogisticRegression())  # 분류기 단계
])

# 파이프라인 학습
pipeline.fit(X_train, y_train)

# 예측
predictions = pipeline.predict(X_test)

```

### 단계 명명 규칙

- 각 단계는 이름과 변환기(estimator)로 구성됩니다.
- 이름은 문자열로, 변환기는 사이킷런의 변환기 또는 추정기 객체입니다.