`GridSearchCV`는 사이킷런(sklearn)에서 하이퍼파라미터 튜닝을 위해 제공하는 도구입니다. 모델 성능을 최적화하기 위해 다양한 하이퍼파라미터 조합을 자동으로 시도하고, 최적의 파라미터를 찾을 수 있도록 도와줍니다.

### 주요 기능

- **하이퍼파라미터 탐색**: 지정된 하이퍼파라미터의 모든 조합에 대해 교차 검증을 수행합니다.
- **교차 검증**: 데이터셋을 여러 폴드로 나누어 각 폴드마다 모델을 학습하고 검증하여 과적합을 방지합니다.
- **모델 선택**: 최적의 하이퍼파라미터 조합을 가진 모델을 자동으로 선택합니다.
- **평가 지표**: 모델 성능을 평가하기 위한 다양한 지표를 지원합니다.

### 주요 매개변수

- `estimator`: 사용할 모델(예: `RandomForestClassifier`, `SVC` 등).
- `param_grid`: 하이퍼파라미터와 그 값들의 딕셔너리입니다. 여러 파라미터의 조합을 시도합니다.
- `scoring`: 모델 성능을 평가할 기준 지표입니다. 기본값은 `None`으로, 이 경우 `estimator`의 `score` 메서드를 사용합니다.
- `cv`: 교차 검증을 위한 폴드 수입니다. 기본값은 `None`으로, 이 경우 5폴드 교차 검증을 사용합니다.
- `n_jobs`: 병렬 처리를 위한 CPU 코어 수입니다. `1`로 설정하면 모든 코어를 사용합니다.
- `verbose`: 실행 중 출력되는 메시지의 상세 정도를 조절합니다. 값이 클수록 더 많은 메시지가 출력됩니다.
- `refit`: 최적의 하이퍼파라미터를 찾은 후, 전체 데이터로 모델을 다시 학습시킬지 여부입니다. 기본값은 `True`입니다.

### 사용 예시

아래 예시는 `RandomForestClassifier`를 사용하여 최적의 하이퍼파라미터를 찾는 과정입니다.

```python
python코드 복사
from sklearn.datasets import load_iris
from sklearn.model_selection import GridSearchCV
from sklearn.ensemble import RandomForestClassifier

# 데이터 로드
iris = load_iris()
X, y = iris.data, iris.target

# 모델과 하이퍼파라미터 그리드 설정
model = RandomForestClassifier()
param_grid = {
    'n_estimators': [10, 50, 100],
    'max_depth': [None, 10, 20, 30],
    'min_samples_split': [2, 5, 10],
}

# GridSearchCV 객체 생성
grid_search = GridSearchCV(estimator=model, param_grid=param_grid, cv=5, n_jobs=-1, verbose=2)

# 모델 학습
grid_search.fit(X, y)

# 최적의 하이퍼파라미터와 성능 출력
print("Best parameters found: ", grid_search.best_params_)
print("Best cross-validation score: {:.3f}".format(grid_search.best_score_))

# 최적의 모델로 예측 수행
best_model = grid_search.best_estimator_
y_pred = best_model.predict(X)

```

### 주요 메서드

- `fit(X, y)`: 주어진 데이터로 그리드 서치를 수행하고 최적의 하이퍼파라미터를 찾습니다.
- `predict(X)`: 최적의 모델을 사용하여 예측을 수행합니다.
- `score(X, y)`: 최적의 모델을 사용하여 점수를 계산합니다.
- `best_params_`: 최적의 하이퍼파라미터 조합을 반환합니다.
- `best_score_`: 교차 검증 동안의 최고 성능 점수를 반환합니다.
- `best_estimator_`: 최적의 하이퍼파라미터로 학습된 모델을 반환합니다.

`GridSearchCV`는 복잡한 모델의 하이퍼파라미터 튜닝을 자동화하고 최적의 모델을 선택하는 데 매우 유용한 도구입니다. 이를 통해 모델의 성능을 극대화하고 과적합을 방지할 수 있습니다.

### pipeline을 이용한 GridSearchCV

```python
from sklearn.datasets import load_iris
from sklearn.model_selection import GridSearchCV
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.ensemble import RandomForestClassifier

iris = load_iris()
X, y = iris.data, iris.target

pipeline = Pipeline([
    ('scaler', StandardScaler()),
    ('classifier', RandomForestClassifier())
])

param_grid = {
    'classifier__n_estimators': [10, 50, 100],
    'classifier__max_depth': [None, 10, 20, 30],
    'classifier__min_samples_split': [2, 5, 10],
}

grid_search = GridSearchCV(pipeline, param_grid, cv=5, n_jobs=-1, verbose=2)

grid_search.fit(X, y)

print("Best parameters found: ", grid_search.best_params_)
print("Best cross-validation score: {:.3f}".format(grid_search.best_score_))

# 최적의 모델로 예측 수행
best_model = grid_search.best_estimator_
y_pred = best_model.predict(X)

```