# <인공지능 기초 8주차 WIL>

transformer까지 따라가보자

## Sequence-to-Sequence (seq2seq)
입력된 시퀀스로부터 다른 도메인의 시퀀스를 출력하는 모델

- encoder  
데이터를 입력받아 정보를 압축한다(context vector) -> 정보를 최대한 보존하며 차원을 낮춘다  
RNN 은닉층의 마지막 시점의 은닉 상태를 decoder에 넘겨준다.  

- decoder  
encoder로부터 받은 정보를 sequence와 같은 형태로 출력  
encoder에서 받은 정보와 입력값을 통해 첫 번째 RNN 셀에서 값을 예측  
이후 예측값과 또 다른 입력을 통해 다음 값을 예측한다.  

- 단점  
정보 압축 과정에서 정보가 손실되어 출력의 정확도가 떨어짐

## Attention 
seq2seq의 단점을 보완하기 위해 나온거  

정보 손실을 최소화 하기 위해 decoder에서 예측값을 뽑아낼 때 encoder의 입력에 사용했던 입력을 참고  
근데 다 참고하는게 아니야 해당 시점에서 필요한 부분을 attention 해서 본다.  

함수로 표현하면?   
Attention(Q, K, V) = Attention Value  
주어진 Query에 대해 모든 Key와의 유사도를 각각 구하고 이 유사도를 Value에 반영  
Query : 현재 timestep의 decoder output  
Key   : 각 timestep별 encoder output  
Value : 각 timestep별 encoder output  

hidden state vector에 선형 변환을 통해 query를 만들고, 만든 query를 인코더의 문장에 대한 행렬과 내적 연산을 하여 유사도를 구할 수 있다  
이후 softmax 연산을 해서 각 단어의 유사도에 대한 가중치 벡터를 얻을 수 있다  

## Transformer
seq2seq에서 RNN을 빼고 Attention만으로 인코더와 디코더를 만들면? -> 더 좋더라~


## 그 외..
내용을 이해하는 것을 목적으로 해서 수식들은 읽어보기만 했습니다.
올려주신 논문 리뷰 사이트랑 [https://wikidocs.net/book/2155] 여기를 참고해서 봤습니당 
논문도 읽어보고 트랜스포머도 이해해보려고 했는데, 과제를 마지막 날에 하느라.. 시간이 된다면 해보려구요
