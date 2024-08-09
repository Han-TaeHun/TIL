`mutual_info_classif`는 Scikit-learn의 `sklearn.feature_selection` 모듈에 포함된 함수로, 주어진 피처(특징)와 타겟 변수 간의 상호 정보량(mutual information)을 계산하여 피처 선택(feature selection)에 유용하게 사용됩니다.

### 상호 정보량 (Mutual Information)

상호 정보량은 두 변수 간의 의존성을 측정하는 값입니다. 이 값이 클수록 두 변수 간의 관계가 강하다는 의미입니다. 상호 정보량은 비선형 관계도 포착할 수 있으며, 두 변수가 독립적이라면 상호 정보량은 0이 됩니다.

### 주요 특징

- **입력 데이터**: `mutual_info_classif` 함수는 피처 행렬 `X`와 타겟 벡터 `y`를 입력으로 받습니다.
- **출력**: 각 피처에 대해 타겟 변수와의 상호 정보량이 계산되며, 이 값이 반환됩니다.
- **범주형 데이터**: `mutual_info_classif`는 연속형과 범주형 데이터 모두에 대해 사용할 수 있습니다. 특히 범주형 타겟 변수에 적합합니다.
- **비선형 관계**: 상호 정보량은 피처와 타겟 변수 간의 비선형 관계도 포착할 수 있습니다.

### 사용법

아래는 `mutual_info_classif`의 간단한 사용 예시입니다.

```python

from sklearn.feature_selection import mutual_info_classif
from sklearn.datasets import make_classification

# 예제 데이터 생성
X, y = make_classification(n_samples=1000, n_features=10, random_state=42)

# 상호 정보량 계산
mi = mutual_info_classif(X, y)

# 결과 출력
print(mi)

```

playground에서 사용했던 예시

```python
mu_train_data = train_data[categorical_col]
mu_train_data = mu_train_data.drop("class", axis=1)
mu_train_data = mu_train_data.fillna("NaN")

encoder = LabelEncoder()
for col in mu_train_data.columns:
    mu_train_data[col] = encoder.fit_transform(mu_train_data[col])

mu_train_data.head()
mu_info = mutual_info_classif(mu_train_data, target, random_state=random_state)
mu_df = pd.Series(mu_info)
mu_df.index = mu_train_data.columns
mu_info = pd.DataFrame(mu_df.sort_values(ascending=False), columns=["categorical"])
mu_info.style.background_gradient("cool")

```

![image](https://github.com/user-attachments/assets/3481c9c6-15d9-4ac0-a4f5-bdf4187f5052)


### 파라미터

- `X`: (n_samples, n_features) 형태의 피처 행렬입니다.
- `y`: (n_samples,) 형태의 타겟 벡터입니다.
- `discrete_features`: 기본값은 `auto`로, X의 피처가 연속형인지 범주형인지를 결정합니다. `True`로 설정하면 모든 피처를 범주형으로 간주하며, `False`로 설정하면 모든 피처를 연속형으로 간주합니다.
- `n_neighbors`: 상호 정보량 추정에 사용하는 이웃의 수를 지정합니다. 기본값은 3입니다.
- `copy`: X를 복사할지 여부를 결정합니다. 기본값은 `True`입니다.
- `random_state`: 난수 시드값입니다. 재현 가능한 결과를 위해 설정할 수 있습니다.

### 출력

- 피처 행렬 `X`의 각 피처에 대해 타겟 변수 `y`와의 상호 정보량이 계산된 값들이 담긴 1차원 배열을 반환합니다.

### 활용

`mutual_info_classif`는 피처 선택을 위해 매우 유용합니다. 상호 정보량이 높은 피처들을 선택함으로써 모델의 성능을 높일 수 있습니다. 특히, 피처 간의 비선형 관계를 탐색할 때 유용합니다.

이 함수는 결정 트리 기반의 피처 선택과 함께 사용될 수 있으며, 불필요한 피처를 제거하고 중요한 피처를 강조하여 모델의 성능을 최적화하는 데 도움을 줍니다.