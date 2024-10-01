# <인공지능 기초 3주차 WIL>

## 무엇을 배웠는가

> 이미지 분류
- 컴퓨터가 주어진 이미지를 보고 어떤 이미지인지 판단하는 작업  
- 이진 분류와 다중 분류로 나뉜다  
- 이미지 분류라고 해서 모두 지도 학습은 아님

> 이미지 데이터의 구조
- 픽셀  
이미지를 구성하는 최소 단위
- 채널  
빛이 통과하는 통로? 흑백이면 1채널, RGB의 경우 3채널
- 해상도  
이미지의 크기, 픽셀 수가 많으면 고해상도

>  기본적인 이미지 분류의 방법
1. 모든 이미지 크기 조정
2. 1차원 벡터로 펼치기
3. 새 이미지와 기존 이미지간 벡터간 거리 계산  
- 맨해튼 거리 :     $|x2 - x1| + |y2 - y1|$
- 유클리드 거리 :   $\sqrt{(x2-x1)^2 + (y2-y1)^2 }$
4. 가장 가까운 이미지로 클래스를 분류

> 선형 분류기
- $f(x, W) = Wx + b$
- N개의 이미지 클래스가 있을 때 행렬 곱을 하면 N x 1 차원의 결과가 나와야 하므로 $x$가 K x 1 차원이라면 $W$는 N x K 차원, $b$는 N x 1 차원이 되어야 한다.
- 결과로 나온 값 중 가장 높게 나온 값으로 분류
- 모든 지식을 가중치에 집어넣음
- 가중치 행렬과 이미지 행렬의 계산으로 유사성에 대한 score을 매기는 방식
- 분류기를 하나만 이용하면 템플릿이 하나로 요약됨 -> 다양한 블록을 쌓아야 한다.

> 기본적인 이미지 분류의 한계
- 물체의 특징이 아닌 픽셀을 통해 구분하기 때문에, 이미지가 옆으로 옮겨지거나 살짝 가려지는 등의 작업이 일어나도 구분을 못 함
- 특징을 통해 분류할 수 있도록 분류기를 만들어야 함

> CNN (Convolutional Neural Network)
- FNN 방식은 인접 픽셀간의 관계를 고려하지 않고 바로 옆의 픽셀이나 멀리 떨어진 픽셀을 똑같이 고려해서 이미지 벡터화 과정에서 정보손실이 발생
- Convolution - Pooling - ... - Convolution - Pooling - Flatten - FNN - Output 
1. Convolution layer = convolution + activation  
convolution : filter를 이미지에 적용하여 이미지의 특징을 뽑아낸다. (슬라이딩 윈도우)  
activation : 선형 여러개 = 선형, 비선형 활성화 함수를 적용 
2.  Pooling layer  
Convolution output 너무 많아서 계산 힘들어 -> 좀 줄이자  
3. Convolution - Pooling 반복 
4. FNN  
공간 구조 망치는것 아닌가? 위의 과정을 통해 이미 들어가 있어서 상관 없다

- 매개변수의 개수  
(input layer 수  x filter 행 x 열 + 1(편향) )x output layer 수  
이거 다 더하기 
## 느낀점
인공지능에 왜 GPU를 쓰는지 조금은 알 것 같다. CNN 과정의 층을 몇개만 더 쌓아도 계산량이 엄청나질 것 같다.  
과제로 부여된 실습의 코드를 보면서 좀 더 이해가 잘 되는 것 같다.  
아직까진 이해할만하다!