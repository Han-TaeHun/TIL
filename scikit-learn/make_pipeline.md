`make_pipeline` 함수는 `Pipeline`의 간편한 대안으로, 단계를 자동으로 명명합니다. 이 방법은 파이프라인을 더 간단하고 빠르게 정의할 수 있게 해줍니다.

### 주요 기능

- **간편한 파이프라인 구성**: 단계 명명을 생략하고 간편하게 파이프라인을 구성할 수 있습니다.
- **자동 명명**: 각 단계의 이름을 자동으로 생성합니다.

### 사용 예시

```python
python코드 복사
from sklearn.pipeline import make_pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression

# 단순히 변환기만 나열
pipeline = make_pipeline(StandardScaler(), LogisticRegression())

# 파이프라인 학습
pipeline.fit(X_train, y_train)

# 예측
predictions = pipeline.predict(X_test)

```