## 1. 원-핫 인코딩 (One-Hot Encoding)

각 범주를 고유한 이진 벡터로 변환합니다.

### 방법

- 각 범주는 서로 다른 열로 분리되며, 해당 범주에 속하는 경우에는 1, 그렇지 않은 경우에는 0이 됩니다.

### 장점

- 모든 범주가 고유하게 표현되므로 범주 간의 순서나 크기 차이를 암시하지 않습니다.
- 특정 범주에 대한 모델의 학습이 분명해집니다.

### 단점

- 범주의 수가 많을 경우 메모리 사용량이 크게 증가할 수 있습니다. (차원의 저주)
- 데이터셋이 희소 행렬 형태가 될 수 있습니다.

### 사용 예

- 범주의 수가 적을 때, 서로 상관관계가 없는 범주를 가진 데이터셋에 적합합니다.
- 예: 색상(빨강, 파랑, 초록), 도시(서울, 뉴욕, 도쿄)

### 메소드

```python
from sklearn.preprocessing import OneHotEncoder

encoder = OneHotEncoder(sparse=False)
one_hot_encoded = encoder.fit_transform(df[['color']])
```

```python
import pandas as pd

df = pd.DataFrame({'color': ['red', 'blue', 'green']})
one_hot_encoded = pd.get_dummies(df['color'])
```

## 2. 라벨 인코딩 (Label Encoding)

각 범주를 고유한 정수 값으로 매핑합니다.

### 방법

- 범주를 정수로 변환하여 한 열에 저장합니다.

### 장점

- 메모리 사용량이 적습니다.
- 범주의 수가 많더라도 데이터를 압축할 수 있습니다.

### 단점

- 범주 간에 순서나 크기 차이가 없는 경우에도 순서를 암시할 수 있습니다.
- 이러한 특성으로 인해 순서를 가진 변수로 오해할 수 있습니다.

### 사용 예

- 범주형 데이터에 순서가 있을 때 적합합니다.
- 예: 등급(A, B, C, D), 경험 수준(초급, 중급, 고급)

```python
from sklearn.preprocessing import LabelEncoder

label_encoder = LabelEncoder()
label_encoded = label_encoder.fit_transform(df['color'])
```

## 3. 순서 인코딩 (Ordinal Encoding)

범주형 데이터가 순서를 가질 때 이를 명시적으로 인코딩합니다.

### 방법

- 각 범주에 순서에 따른 정수값을 할당합니다.

### 장점

- 범주 간 순서나 비교 가능성이 있을 때 적합합니다.
- 데이터의 순서 정보를 유지할 수 있습니다.

### 단점

- 잘못 사용될 경우, 모델이 순서를 가정하지 않는 경우 문제가 될 수 있습니다.

### 사용 예

- 범주 간의 자연스러운 순서가 있는 경우.
- 예: 영화 평점(별 1개, 별 2개, 별 3개)

```python
from sklearn.preprocessing import OrdinalEncoder
df = pd.DataFrame({'size': ['small', 'medium', 'large']})
ordinal_encoder = OrdinalEncoder(categories=[['small', 'medium', 'large']])
ordinal_encoded = ordinal_encoder.fit_transform(df[['size']])
```

## 4. 이진 인코딩 (Binary Encoding)

각 범주를 정수로 변환한 후, 이진수로 변환하여 비트를 원-핫 인코딩 방식으로 표현합니다.

### 방법

- 정수 인코딩 후 이진수로 변환하여 비트 수만큼의 열로 나누어 표현합니다.

### 장점

- 높은 범주 수에도 원-핫 인코딩보다 메모리 사용량이 적습니다.
- 정수 인코딩보다 순서 문제를 덜 초래합니다.

### 단점

- 원-핫 인코딩에 비해 직관적이지 않을 수 있습니다.

### 사용 예

- 매우 많은 범주를 가진 데이터에 적합합니다.
- 예: 사용자 ID, 제품 ID

```python
import category_encoders as ce

df = pd.DataFrame({'color': ['red', 'blue', 'green']})
binary_encoder = ce.BinaryEncoder(cols=['color'])
binary_encoded = binary_encoder.fit_transform(df)
```

## 5. 타깃 인코딩 (Target Encoding)

범주형 변수를 타깃 변수와 연관된 값으로 대체합니다.

### 방법

- 각 범주에 대해 타깃 변수의 평균, 중위수 등의 통계량으로 변환합니다.

### 장점

- 타깃 변수와의 상관관계를 잘 반영할 수 있습니다.
- 범주 수가 많아도 처리 가능하며, 메모리 사용량이 적습니다.

### 단점

- 데이터 누출(leakage) 문제 발생 가능성.
- 학습 데이터와 평가 데이터 간의 분포 차이로 인해 모델 성능이 저하될 수 있습니다.

### 사용 예

- 타깃 변수와의 상관관계를 반영하고 싶은 경우.
- 예: 고객 분류(고객 등급 -> 평균 지출 금액)

```python
import category_encoders as ce

df = pd.DataFrame({'category': ['A', 'B', 'A', 'B'], 'target': [1, 2, 3, 4]})
target_encoder = ce.TargetEncoder(cols=['category'])
df['category_encoded'] = target_encoder.fit_transform(df['category'], df['target'])
```

## 6. 빈도 인코딩 (Frequency Encoding)

각 범주를 데이터 내에서 나타나는 빈도로 대체합니다.

### 방법

- 각 범주에 대한 빈도를 계산하여 해당 값을 부여합니다.

### 장점

- 단순하지만 강력한 방법입니다.
- 메모리 사용량이 적으며, 일부 예측 문제에서 유용할 수 있습니다.

### 단점

- 빈도 정보가 모델에 필요한 정보인지에 따라 효과가 달라질 수 있습니다.

### 사용 예

- 범주의 빈도가 중요한 역할을 할 가능성이 있는 경우.
- 예: 특정 제품의 판매 수량

```python
df = pd.DataFrame({'category': ['A', 'B', 'A', 'C', 'B', 'A']})
frequency_encoded = df['category'].map(df['category'].value_counts())
```