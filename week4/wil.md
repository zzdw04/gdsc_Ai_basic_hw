# <인공지능 기초 4주차 WIL>

## 무엇을 배웠는가

### Loss Function  

더 정확한 예측을 위해 현재 예측값과 실제 값과의 차이를 수치화 하여 이를 바탕으로 가중치를 업데이트 하기 위한 함수
#### SVM Loss  

Support Vector Machine의 Hinge Loss  
SVM : 최적의 결정 경계를 찾는 알고리즘, 허용가능한 범위 내에서 margin을 크게 만드는 것이 목표
  - $L_i = \sum_{i{\ne}y_i}max(0, s+j-s_{y_i} + 1)$  

#### Cross Entropy Loss  

정답이 one-hot vector로 나타내져있고, 출력값을 확률(확신도)로서 해석할 때 $\rarr$  softmax 함수  
 - $L_i = -\sum_{i = 1}^cy_ilog(p_i)$   
   잘 된 예측이라면 p값이 클 수록(1에 가까울수록) -log 값이 0에 가까워지고 반면에 잘 못된 예측이라면 -log값이 커짐
### Regularization  
overfitting 문제를 해결하기 위해 parameter에 대한 term을 추가하여 가중치 w가 작아지도록 한다.  
- L2 Regularization  
$cost = \frac{1}{n}\sum_{i = 1}^n\{L(y_i, \hat{y_i}) + \frac{\lambda}{n}w^2\}$  
매끄러운 그래프를 원할때, 큰 가중치에 더 큰 패널티를 부과  
모든 특성이 적당히 기여하도록

- L1 Regularization  
$cost = \frac{1}{n}\sum_{i = 1}^n\{L(y_i, \hat{y_i}) + \frac{\lambda}{n}|w|\}$  
분류기가 복잡한 것 같을 때, 가중치에 0이 많도록 해서 단순화 

### Optimization  
Loss fuction이 줄어들도록 조정하는 방법  
Loss fuction의 최소지점을 찾아가는 것이 목표

Momentum(관성) : 이전 업데이트 방향을 고려하여 업데이트  
Adaptive Learning rate : 과거의 정보를 활용하여 파라미터마다 서로 다른 학습률 사용  
초기에 높은 학습률을 사용하면 빠르게 최적점 근처로 접근이 가능하며 적절한 시점에 학습률을 높인다면 지역 최소(극소값)에서 벗어날 수 있다.  
$\rarr$ 극솟값에서도 미분계수가 0이기 때문에 미분계수가 0이어도 최솟값이 아닐 수 있음

## 더 알아봐야 할 것 같은 부분
L2 Regularization에서 제곱해서 더 큰 패널티를 부여하는건 알겠는데 그 외의 부분이 좀 크게 와닿지 않는다. 항을 더해서 가중치가 작아진다는점이나 L1에서 가중치에 0이 많도록 한다는점? 이게 좀 와닿지 않는다.

Optimization 과정을 구체적으로 더 알아보면 좋을 것 같다. 