# <인공지능 기초 7주차 WIL>

## Object Detection
어느 객체가 어디에 있을까?

## Ideation
Image Classification + 객체를 분류하는 모델  
객체를 분류해 낸 뒤 이미지 분류를 통해 이 객체가 무엇인지 알아내자!

## Two-Stage Detector
두 단계에 걸쳐서 Object Detection을 수행  

- NMS : 박스로 만든게 너무 많아서 겹치는 정도 비교해서 너무 많이 겹친다 == 같은 객체를 가리키고 있을 확률이 높다! -> 없애버려  
겹치는 정도 (IOU) = 교집합 / 합집합  
근데 애초에 한 영역에 여러 객체가 있는경우 좋은 bbox를 없애기도 함

### R-CNN
1. selective search(이건 그냥 계산임)로 ROI(흥미 구역) 뽑기
2. region size 고정된 크기로 wrapping(사이즈 조정, 문제 생길 수도 있는데 그냥 해)
3. CNN
4. Support Vector Machine으로 분류 + Bbox Regression  
-> 2000번 CNN은 힘들어

### Fast R-CNN
CNN과 resize 순서를 바꿔
분류기로 SVM -> linear,  CNN에서 fc-layer는 안씀
convNet 이후 feature map을 뽑아 ROI pooling 하여 객체를 구분
- ROI pooling  
wraping 과정에서의 데이터 손실 -> 성능 저하
적당히 구역을 나누고 그 구역에서 pooling을 진행 
ex) 8x8 -> 4x4 4개로 쪼개고 한 구역당 pooling -> 2x2를 얻을 수 있다.

### Faster R-CNN
Fast R-CNN의 selective search 단계 대신 RPN 적용

## One-Stage Detector

### YOLO 
앞에서 나온 객체를 탐지하고, 분류를 하는 과정을 한번에 수행  
yolo v1은 단순한데 정확도가 떨어진다

### FPN
다양한 크기의 객체를 탐지하는 방법 중 하나  
pyramid : CNN 과정에서 얻은 여러가지 해상도의 이미지를 쌓음
