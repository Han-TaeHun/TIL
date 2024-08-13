[StratifiedKFold](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.StratifiedKFold.html)

`StratifiedKFold`는 `scikit-learn`에서 제공하는 교차 검증 방법 중 하나로, 각 폴드가 원래 데이터셋의 클래스 분포를 유지하도록 데이터를 나눕니다. 이를 통해 클래스 불균형 문제를 해결할 수 있습니다. 예를 들어, 분류 문제에서 각 폴드에 클래스가 고르게 분포되도록 합니다. 

**유용한 분류기에 속하는 것 같음**

**일단 이거 쓰는게.. 좋은 듯** 

### `StratifiedKFold` 사용 방법

### 기본 사용법

```python
python코드 복사
from sklearn.model_selection import StratifiedKFold

# 예제 데이터셋 (features, labels)
X = [[1, 2], [3, 4], [1, 2], [3, 4], [1, 2], [3, 4], [1, 2], [3, 4]]
y = [0, 0, 1, 1, 1, 1, 0, 0]

# StratifiedKFold 객체 생성
skf = StratifiedKFold(n_splits=3)

# 교차 검증을 위한 폴드 생성
for train_index, test_index in skf.split(X, y):
    print("TRAIN:", train_index, "TEST:", test_index)
    X_train, X_test = [X[i] for i in train_index], [X[i] for i in test_index]
    y_train, y_test = [y[i] for i in train_index], [y[i] for i in test_index]
    # 모델 학습 및 평가

```

### 주요 파라미터

- `n_splits`: 폴드의 수. 데이터를 몇 개의 폴드로 나눌지 결정합니다.
- `shuffle`: 데이터를 나누기 전에 셔플할지 여부를 지정합니다. 기본값은 `False`입니다.
- `random_state`: `shuffle=True`일 때 데이터 셔플링의 시드를 설정하여 재현성을 확보합니다.

### 예시

다음은 `StratifiedKFold`를 사용하여 분류 모델을 학습하고 평가하는 예제입니다.

```python
python코드 복사
from sklearn.datasets import load_iris
from sklearn.model_selection import StratifiedKFold
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score

# 데이터셋 로드
iris = load_iris()
X, y = iris.data, iris.target

# StratifiedKFold 객체 생성
skf = StratifiedKFold(n_splits=5, shuffle=True, random_state=42)

# 교차 검증
accuracies = []

for train_index, test_index in skf.split(X, y):
    X_train, X_test = X[train_index], X[test_index]
    y_train, y_test = y[train_index], y[test_index]

    # 모델 학습
    model = LogisticRegression(max_iter=200)
    model.fit(X_train, y_train)

    # 예측 및 평가
    y_pred = model.predict(X_test)
    acc = accuracy_score(y_test, y_pred)
    accuracies.append(acc)

print("Accuracy scores for each fold: ", accuracies)
print("Mean accuracy: ", sum(accuracies) / len(accuracies))

```

### `StratifiedKFold`의 장점

- **클래스 불균형 문제 해결**: 각 폴드에 클래스가 고르게 분포되므로, 클래스 불균형 데이터셋에서도 안정적인 성능 평가가 가능합니다.
- **재현성**: `shuffle`과 `random_state`를 설정하여 동일한 폴드 분할을 재현할 수 있습니다.

![선택 영역_177](https://github.com/user-attachments/assets/27c9bfa7-dcdb-499d-8f89-6f4f5fb4bfb1)


본적으로 **KFold** 교차 검증 반복자는 데이터 포인트 클래스나 그룹을 고려하지 않습니다. 

- `StratifiedKFold`각 **클래스의 샘플 비율을 유지**합니다.
- `GroupKFold`동일한 그룹이 두 개의 서로 다른 폴드에 나타나지 않도록 합니다.
- `StratifiedGroupKFoldGroupKFold`계층화된 폴드를 반환하려고 시도하는 동안 제약 조건을 유지합니다

![선택 영역_178](https://github.com/user-attachments/assets/279a66b5-0c78-44f9-a93d-a8de1168a488)

### GroupKFold

- **특징:**
    - 데이터셋을 그룹 단위로 나누는 데 사용됩니다.
    - 같은 그룹에 속한 데이터는 훈련 세트와 검증 세트에 중복되지 않도록 보장합니다.
    - 그룹의 크기나 데이터의 클래스 분포는 고려하지 않습니다.
- **사용 예시:**
    - 같은 환자에게서 나온 의료 데이터.
    - 동일 사용자가 여러 번 관측된 온라인 광고 데이터.
- **사용법:**
    
    ```python
    python코드 복사
    from sklearn.model_selection import GroupKFold
    
    X = ...  # 데이터
    y = ...  # 타겟
    groups = ...  # 그룹
    
    gkf = GroupKFold(n_splits=5)
    
    for train_index, test_index in gkf.split(X, y, groups):
        X_train, X_test = X[train_index], X[test_index]
        y_train, y_test = y[train_index], y[test_index]
    
    ```
    

### StratifiedGroupKFold

- **특징:**
    - `GroupKFold`의 기능에 층화(stratification) 기능을 추가한 방법입니다.
    - 그룹별로 나누면서 각 폴드가 전체 데이터의 클래스 분포를 반영하도록 합니다.
    - 그룹 내 데이터가 폴드 간에 겹치지 않게 유지하면서도 클래스 간 불균형을 완화할 수 있습니다.
- **사용 예시:**
    - 그룹화된 의료 데이터에서 각 환자(그룹)의 다양한 검사 결과 중 타겟 변수가 불균형할 때.
    - 동일 사용자가 여러 번 관측된 온라인 광고 데이터 중 타겟 변수가 불균형할 때.
- **사용법:**
    
    ```python
    python코드 복사
    from sklearn.model_selection import StratifiedGroupKFold
    
    X = ...  # 데이터
    y = ...  # 타겟
    groups = ...  # 그룹
    
    sgkf = StratifiedGroupKFold(n_splits=5)
    
    for train_index, test_index in sgkf.split(X, y, groups):
        X_train, X_test = X[train_index], X[test_index]
        y_train, y_test = y[train_index], y[test_index]
    
    ```
    

### StratifiedKFold

- **특징:**
    - 데이터셋을 층화하여 나누는 데 사용됩니다.
    - 각 폴드가 전체 데이터의 클래스 분포를 반영하도록 합니다.
    - 그룹화된 데이터를 고려하지 않고 개별 데이터 포인트를 사용합니다.
- **사용 예시:**
    - 클래스 불균형이 있는 데이터셋에서 모델의 평가를 위해 사용합니다.

### 요약

- `GroupKFold`: 그룹화된 데이터에서 그룹 단위로 폴드를 나눕니다. 클래스 분포를 고려하지 않습니다.
- `StratifiedGroupKFold`: 그룹화된 데이터에서 그룹 단위로 폴드를 나누면서도 클래스 분포를 유지합니다.
- `StratifiedKFold`: 그룹을 고려하지 않고 데이터를 나누며, 각 폴드에서 클래스 분포를 유지합니다.