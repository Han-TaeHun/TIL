- 앙상블(Ensemble)**은 머신러닝에서 여러 개의 모델을 결합하여 하나의 예측 결과를 만드는 방법을 말합니다. 개별 모델보다 더 나은 예측 성능을 얻기 위해 사용됩니다. 앙상블 기법은 다양한 모델의 강점을 결합하고, 개별 모델의 단점을 보완할 수 있어, 일반적으로 더 높은 정확도와 신뢰성을 제공합니다.

### 앙상블의 주요 기법

### **배깅 (Bagging)**:

- 배깅은 동일한 유형의 모델을 여러 개 학습시키기 위해 훈련 데이터를 무작위로 샘플링하여 여러 개의 하위 데이터셋을 만듭니다.
- **같은 알고리즘** 유형의 모델들이 이지만 데이터 샘플링을 다르게 하여 **학습 데이터셋이 각각 다르다(단 교차 검증과 다르게 데이터 세트간 중첩을 허용).**
- Categorical Data 는 투표방식voting으로 집계,
- Continuous Data는 평균으로 집계
- 각 모델은 다른 데이터셋을 사용하여 독립적으로 학습됩니다.
- 최종 예측은 각 모델의 예측 결과를 평균하거나 다수결 투표를 통해 결정합니다.
- 대표적인 예: 랜덤 포레스트(Random Forest) (대부분 **결정 트리 알고리즘**을 사용)

https://www.datacamp.com/tutorial/what-bagging-in-machine-learning-a-guide-with-examples

![선택 영역_182](https://github.com/user-attachments/assets/be182af2-1fa3-47ee-9adf-3c01470f1983)

![선택 영역_183](https://github.com/user-attachments/assets/aa6d2895-7976-4025-9d49-f3cd01710383)

### **부스팅 (Boosting)**:

- 부스팅은 일련의 모델을 순차적으로 학습시켜 예측 성능을 향상시키는 방법입니다.
- 각 모델은 이전 모델이 잘못 예측한 사례에 가중치를 두어 학습합니다. (가중치를 부여해서 틀린 부분을 더 잘 맞출 수 있도록 하는 것)
- 최종 모델은 모든 모델의 예측 결과를 가중합하여 결정합니다.
- 대표적인 예: AdaBoost, Gradient Boosting Machines (GBM), XGBoost, LightGBM.

출처 https://en.wikipedia.org/wiki/Boosting_(machine_learning)
![선택 영역_184](https://github.com/user-attachments/assets/643942b8-7455-4300-aed4-b30995c2897e)



### **스태킹 (Stacking)**:

- 스태킹은 여러 개의 모델의 예측 결과를 사용하여 상위 메타 모델을 학습시키는 방법입니다.
- 각 모델의 예측 결과를 새로운 특성으로 사용하여 메타 모델을 학습합니다.
- 최종 예측은 메타 모델의 예측 결과를 사용합니다.

출처 - https://dacon.io/codeshare/4651
![선택 영역_185](https://github.com/user-attachments/assets/88a6f3f7-a6a0-4e23-8060-54852dc85961)


### **보팅 (Voting)**:

- 보팅은 투표를 통해 최종 예측 결과를 결정하는 방식… 배깅과 굉장히 비슷한 느낌…
- 투표라는 것이 각 알고리즘이 내는 결과값을 기준으로 정하는 거다 ㅎㅎ
- **다른 알고리즘**을 가진 분류기가 **같은 데이터셋**을 기반으로 학습
- 주로 분류 문제에 사용
- 서로 다른 유형의 여러 분류기를 결합하여 최종 예측을 생성하는 기법
    
    출처 -  https://continuous-development.tistory.com/entry/MLDL-앙상블-학습-Ensemble-Learning-2-Voting보팅이란-1?pidx=0
    
    
    ![선택 영역_186](https://github.com/user-attachments/assets/80271737-4cd7-4e07-84fc-7cb005eb33ca)
    
- **하드 보팅(Hard Voting)**: 각 모델의 예측 중 가장 많이 예측된 클래스가 최종 예측이 됩니다.(결국 다수결)
- **소프트 보팅(Soft Voting)**: 각 모델의 예측 확률의 평균을 계산하여 가장 높은 확률의 클래스가 최종 예측이 됩니다. (평균으로 정함)
    
    출처 -  https://continuous-development.tistory.com/entry/MLDL-앙상블-학습-Ensemble-Learning-2-Voting보팅이란-1?pidx=0
    ![선택 영역_187](https://github.com/user-attachments/assets/aec97111-d54a-4bb8-99ad-65ffed71e719)

### 앙상블의 장점

1. **성능 향상**: 여러 모델을 결합하여 더 높은 예측 정확도를 얻을 수 있습니다.
2. **강건성**: 개별 모델의 오류가 상쇄되므로 안정성이 높아집니다.
3. **일반화 능력**: 과적합을 방지하고 모델의 일반화 능력을 향상시킬 수 있습니다.

### 앙상블의 단점

1. **복잡성**: 여러 모델을 학습하고 결합하는 과정이 복잡할 수 있습니다.
2. **연산 비용**: 여러 모델을 사용하기 때문에 계산 자원이 더 많이 필요할 수 있습니다.
3. **해석력 부족**: 앙상블 모델은 개별 모델에 비해 해석하기 어렵습니다.

앙상블은 머신러닝에서 매우 강력한 기법이며, 많은 경진대회와 실무 프로젝트에서 높은 성능을 내기 위해 자주 사용됩니다. 적절한 앙상블 기법을 선택하고 조합하는 것은 모델링의 중요한 요소입니다.