# <인공지능 기초 6주차 WIL>

## CNN  
- FNN - 인접한 데이터간의 상관관계가 무너진다  
 -> 필터를 통해 feature map을 뽑아 데이터 간의 상관관계 유지  

## Activation Function  
- 활성화 함수 없이 여러 층을 쌓게 되면 한 층을 쌓는 것과 다르지 않다.  
- $f(x) = W_2(W_1x + b_1) + b_2 = Wx + b$  
- 따라서 비선형 함수를 추가해서 복잡한 모델을 만든다.  

## Batch Normalization  
- 정규화 : 데이터에 평균을 빼고 표준편차로 나누기  
- 과도한 스케일을 가진 특성을 조절하고, 학습 속도를 늘릴 수 있다.  
- 학습 과정에서 정규화 했던 데이터의 분포가 달라질 수 있어서 학습 과정마다 정규화를 해야 함  

## Transfer learning 전이학습
- 지도학습을 위한 라벨링된 데이터셋은 비싸다!
- 이미 학습된 모델의 지식을 활용
- Parameter-Efficient Fine-Tuning with Low-Rank Adaptation(LoRA) :  
  파라미터 전체를 수정하지 않아서 대형 모델에서 필요한 부분만을 파인튜닝 할 때 좋다. 

## Knowledge Distillation  
- 학습된 모델을 다른 모델에 전달