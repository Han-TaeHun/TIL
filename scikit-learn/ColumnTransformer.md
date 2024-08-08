`ColumnTransformer`는 서로 다른 전처리 단계를 데이터셋의 각 열에 개별적으로 적용할 수 있도록 해주는 도구입니다. 이를 통해 수치형, 범주형 등 서로 다른 데이터 타입을 가진 특성들을 별도로 처리할 수 있습니다.

### 주요 기능

- **열별 전처리**: 각 열에 대해 다른 전처리 과정을 적용할 수 있습니다.
- **다양한 전처리 지원**: 스케일링, 인코딩, 결측치 처리 등 여러 전처리 단계를 결합할 수 있습니다.
- **복합 전처리**: 여러 전처리기를 하나의 파이프라인에 결합할 수 있습니다.

### 사용 예시

```python
python코드 복사
from sklearn.compose import ColumnTransformer
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler, OneHotEncoder
from sklearn.impute import SimpleImputer

# 수치형 특성에 대한 전처리 파이프라인
numeric_features = ['numerical_feature1', 'numerical_feature2']
numeric_transformer = Pipeline(steps=[
    ('imputer', SimpleImputer(strategy='median')),
    ('scaler', StandardScaler())
])

# 범주형 특성에 대한 전처리 파이프라인
categorical_features = ['categorical_feature']
categorical_transformer = Pipeline(steps=[
    ('imputer', SimpleImputer(strategy='constant', fill_value='missing')),
    ('onehot', OneHotEncoder(handle_unknown='ignore'))
])

# ColumnTransformer 설정
preprocessor = ColumnTransformer(
    transformers=[
        ('num', numeric_transformer, numeric_features),
        ('cat', categorical_transformer, categorical_features)
    ]
)

# 전체 파이프라인 설정
pipeline = Pipeline(steps=[
    ('preprocessor', preprocessor),
    ('classifier', LogisticRegression())
])

pipeline.fit(X_train, y_train)
predictions = pipeline.predict(X_test)

```

### ColumnTransformer의 transform 단계

- 각 열에 대해 설정된 변환기(transformer)를 적용합니다.
- 변환된 데이터를 결합하여 새로운 데이터셋을 생성합니다.