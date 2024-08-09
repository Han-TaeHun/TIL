`LabelEncoder`는 Scikit-learn의 `sklearn.preprocessing` 모듈에 포함된 클래스입니다. 이 클래스는 **범주형(카테고리형)** 데이터를 **숫자형(label)**으로 변환하는 데 사용됩니다. 머신 러닝 모델은 보통 숫자형 데이터를 다루기 때문에, 텍스트 또는 범주형 데이터를 모델에 사용할 수 있는 형태로 변환하는 과정이 필요합니다.

### `LabelEncoder`의 주요 기능

- **범주형 데이터를 정수로 변환**: 예를 들어, ["apple", "banana", "orange"] 같은 범주형 데이터를 [0, 1, 2] 같은 숫자형 데이터로 변환할 수 있습니다.
- **유일한 값 매핑**: 동일한 값은 항상 같은 숫자로 변환됩니다. 예를 들어, "apple"은 항상 0으로, "banana"는 항상 1로 변환됩니다.
- **역변환 가능**: 변환된 숫자를 다시 원래의 범주형 데이터로 변환할 수 있습니다.

### 사용법

```python
python코드 복사
from sklearn.preprocessing import LabelEncoder

# 샘플 데이터
fruits = ["apple", "banana", "orange", "apple", "orange"]

# LabelEncoder 객체 생성
label_encoder = LabelEncoder()

# 범주형 데이터를 정수로 변환 (피팅과 변환 동시 수행)
encoded_fruits = label_encoder.fit_transform(fruits)

print("Encoded labels:", encoded_fruits)  # [0 1 2 0 2]

# 인코딩된 데이터를 다시 원래 범주형 데이터로 역변환
decoded_fruits = label_encoder.inverse_transform(encoded_fruits)

print("Decoded labels:", decoded_fruits)  # ['apple' 'banana' 'orange' 'apple' 'orange']

```

### 따로 전처리하는거 테스트

```python
encoder = LabelEncoder()

# target 전처리 
y_train_ecoded = encoder.fit_transform(y_train)
y_train_ecoded = pd.DataFrame(y_train_ecoded, columns=["class"])
# y_train_ecoded.head()
encoder.inverse_transform(y_train_ecoded)

# ouput
#array(['e', 'p', 'e', ..., 'p', 'e', 'p'], dtype=object)

y_train_test = encoder.fit_transform(X_train["season"])
y_train_test = pd.DataFrame(y_train_test, columns=["season"])
y_train_test.head()
encoder.inverse_transform(y_train_test)

# ouput
#array(['a', 'w', 'w', ..., 'a', 'u', 'u'], dtype=object)
```

### 주요 메서드

- `fit(y)`: 데이터를 학습(fit)하여 내부적으로 고유한 범주와 그에 대응하는 레이블을 기억합니다.
- `transform(y)`: 학습된 레이블을 사용하여 데이터를 변환합니다. 즉, 범주형 데이터를 숫자로 변환합니다.
- `fit_transform(y)`: `fit`과 `transform`을 한 번에 수행합니다.
- `inverse_transform(y)`: 숫자로 변환된 레이블을 다시 원래의 범주형 데이터로 변환합니다.
- `classes_`: 학습된 고유한 범주(클래스)를 반환합니다.

### 주의사항

- **LabelEncoder는 범주형 타겟 데이터에 주로 사용**: 피처의 경우, `OneHotEncoder`를 사용하는 것이 일반적입니다. `LabelEncoder`는 타겟 값이 범주형일 때 주로 사용됩니다.
- **중복 사용**: `LabelEncoder`를 두 번 사용하면 동일한 객체에서 이전에 학습된 데이터를 덮어씁니다. 새로 생성된 `LabelEncoder` 객체로 다른 범주형 데이터를 처리할 때, 이전에 변환했던 정보는 유지되지 않습니다.

따라서 서로 다른 범주형 데이터를 각각 인코딩할 때는 별도의 `LabelEncoder` 객체를 사용하는 것이 좋습니다.

### 1. `LabelEncoder`는 1차원 데이터에 사용됩니다.

`LabelEncoder`는 **한 번에 하나의 특성(열)**만 변환할 수 있습니다. 즉, 다차원 데이터(여러 열을 가진 데이터프레임)에서는 사용하기 어렵습니다. 파이프라인에서 여러 열을 변환할 때 `LabelEncoder`를 사용하면 오류가 발생할 수 있습니다.

### 2. 범주형 특성을 수치형으로 변환 시 문제

`LabelEncoder`는 범주형 데이터를 단순히 정수로 변환합니다. 예를 들어, `['red', 'green', 'blue']`가 있을 때, `LabelEncoder`는 이를 `[0, 1, 2]`로 변환합니다. 이 정수 값은 모델에 의해 순서 정보로 해석될 수 있어 문제가 될 수 있습니다.

예를 들어, 모델이 'red'를 0, 'green'을 1, 'blue'를 2로 인식하면서 'green'이 'red'보다 크고 'blue'는 'green'보다 크다고 잘못 해석할 수 있습니다. 이 경우, 의도하지 않은 순서 정보가 모델에 포함될 수 있어 성능에 악영향을 줄 수 있습니다.

### 3. `Pipeline` 내 사용 문제

`LabelEncoder`는 다차원 데이터에서 직접적으로 사용할 수 없기 때문에, `Pipeline`이나 `ColumnTransformer` 내에서 여러 열을 동시에 변환하는 작업에 적합하지 않습니다.

### 대안: `OneHotEncoder` 또는 `OrdinalEncoder`

- **`OneHotEncoder`**: 범주형 데이터를 one-hot 형식으로 변환합니다. 각 범주를 개별 이진 열로 변환하여 순서 정보가 없는 이진 값을 생성합니다.
- **`OrdinalEncoder`**: 여러 열을 변환할 수 있고, 범주형 데이터를 정수로 변환하지만, 이를 사용할 때는 데이터에 순서가 있는 경우에만 사용하는 것이 좋습니다.

### 요약

`LabelEncoder`는 단순한 작업에는 유용하지만, 다차원 데이터와 파이프라인 작업에는 적합하지 않습니다. 특히, `Pipeline`이나 `ColumnTransformer`와 함께 사용할 때는 `OneHotEncoder` 또는 `OrdinalEncoder`를 사용하는 것이 일반적으로 더 적절합니다.