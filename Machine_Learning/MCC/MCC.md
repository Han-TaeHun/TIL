Matthews Correlation Coefficient(MCC)는 이진 분류의 성능을 측정하는 지표 중 하나로, 예측의 정확성을 평가하는 데 사용됩니다. MCC는 예측과 실제 값 간의 상관 관계를 나타내며, 예측이 무작위로 이루어진 것과 비교해 얼마나 정확한지를 나타내는 정량적 지표입니다.

MCC는 -1에서 1 사이의 값을 가지며, 값이 1에 가까울수록 예측이 완벽하게 맞았음을, 0에 가까울수록 무작위 추측에 가까움을, -1에 가까울수록 예측이 완전히 틀렸음을 의미합니다.

### MCC 계산 공식

MCC는 다음과 같은 공식으로 계산됩니다:

$$
\text{MCC} = \frac{{(TP \times TN) - (FP \times FN)}}{{\sqrt{{(TP + FP)(TP + FN)(TN + FP)(TN + FN)}}}}
$$

여기서:

- **TP (True Positives)**: 실제 Positive인 경우를 Positive로 예측한 수
- **TN (True Negatives)**: 실제 Negative인 경우를 Negative로 예측한 수
- **FP (False Positives)**: 실제 Negative인 경우를 Positive로 예측한 수
- **FN (False Negatives)**: 실제 Positive인 경우를 Negative로 예측한 수

![1682170243661](https://github.com/user-attachments/assets/32231b64-6b8c-445f-9f75-a862ad16d2e2)
g)

### Python에서 MCC 계산

`scikit-learn` 라이브러리의 `matthews_corrcoef` 함수를 사용하여 쉽게 MCC를 계산할 수 있습니다. 예를 들어, 실제 라벨과 예측 라벨이 주어졌을 때 MCC를 계산하는 방법은 다음과 같습니다:

```python
python코드 복사
from sklearn.metrics import matthews_corrcoef

# 실제 값과 예측 값 예시
y_true = [1, 0, 1, 1, 0, 1, 0, 0, 1, 0]
y_pred = [1, 0, 1, 0, 0, 1, 1, 0, 1, 0]

# MCC 계산
mcc = matthews_corrcoef(y_true, y_pred)
print(f'Matthews Correlation Coefficient: {mcc}')
```

### 해석

- **MCC = 1**: 완벽한 예측 (모든 양성과 음성을 정확하게 예측)
- **MCC = 0**: 무작위 예측 (양성, 음성 예측이 무작위로 이루어짐)
- **MCC = -1**: 완전히 잘못된 예측 (모든 양성과 음성을 정확하게 반대로 예측)

MCC는 클래스 불균형 문제가 있는 데이터셋에서도 좋은 성능 지표로 간주됩니다. 이는 정확도(accuracy)나 F1 스코어와는 달리, 양성과 음성 클래스의 불균형을 반영하는 지표이기 때문입니다.