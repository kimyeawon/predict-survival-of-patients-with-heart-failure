# predict-survival-of-patients-with-heart-failure
Title: predict survival of patients with heart failure

Members: 김예원(건축학과, yeawon0515@hanyang.ac.kr)
         신승국(수리데이터사이언스학과, tlstmdrnr135@naver.com)
         장위신(기계공학과,weixin0713@hanyang.ac.kr）
         
I. Proposal (Option 1or 2)
심부전이란 심장의 구조적 또는 기능적 이상으로 인해 심장이 혈액을 받아들이는 이완 기능이나 짜내는 수축 기능이 감소하여 신체 조직에 필요한 혈액을 제대로 공급하지 못해 발생하는 질환군을 말한다. 발생 원인은 스트래스, 식습관, 음주 등 매우 다양하게 나타나며 바쁜 사회를 살아가는 현대인들에게 발생률이 점점 증가하고 있다. 또한 이 질환은 생명과 직결되는 매우 중요한 과제임으로 이에 대한 예측은 오늘날 매우 중요한 과제라고 할 수 있다. 
딥러닝은 주워진 데이터를 토대로 예측을 수행하는 매우 강력한 수단중 하나로, 많은 사람들에게 관심을 받으며 빠른 속도로 변화하고 있다. 또한 다양한 산업과 직군속에서 활용 및 가치를 창출하고 있으며 따라서 이에대한 역량을 갖추는 것은 매우 중요한 일중 하나이다. 우리는 DNN 모델의 구조를 파악하고 심부전에 의한 사망 여부 예측을 통해 간단한 문제를 해결한 후 다른 여러 머신러닝 기법들과 비교를 통해 딥러닝의 특성을 파악함으로써 이러한 역량을 갖출수 있고자 한다.

II. Datasets
출처: https://www.kaggle.com/datasets/rabieelkharoua/predict-survival-of-patients-with-heart-failure
변수 설명:
    aage 나이
    anaemia 빈혈
    creatinine_phosphokinase 크레아티닌 인산화효소
    diabetes 당뇨여부
    ejection_fraction 심장 피 분출률
    high_blood_pressure 고혈압 여부
    platelets 혈소판 수(kiloplatelets/mL)
    serum_creatinine 혈청 크레아티닌(mg/dL)
    serum_sodium 혈청 나트륨(mEq/L)
    sex 성별(0: 여성, 1: 남성)
    smoking 흡연 여부
    time 환자 상태가 모니터된 시간(day)

데이터 개수: 299개
독립변수 개수: 12개
종속변수: DEATH_EVENT



III. Methodology
-explaining your choice of algorithms (methods)
1. ANN(인공신경망)이란?
인공신경망(ANN)이란 동물 뇌의 신경망을 모방해 만든 알고리즘으로, 뉴런을 모방한 노드들이 연결되어 있는 형태이다. 일반적으로 각각 한 개의 입력층과 출력층, 은닉층을 가진다.


2. DNN이란?
가장 기본적인 형태인 ANN을 응용하기 위하여 은닉층의 수를 2개 이상으로 늘린 신경망 구조를 가진 모델인 DNN(Deep Neural Network)을 이용한다.

![DNN i](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/74c5fffd-904b-4780-9dc7-c88548cfb778)


3. DNN의 수학적 베이스
DNN은 은닉층의 수, 노드의 수에 따라 많은 bias과 weight를 가지게 되며 weight의 경우 각 레이어의 노드의 곱, bias은 각 레이어의 노드의 합만큼의 갯수를 가지게 된다. 이들은 chain rule을 이용하여 loss 값을 줄이는 방향으로 학습을 진행하여 결과적으로 들어오는 변수에따라 weight와 bias가 비선형적으로 변하게 된다.
chain rule은 합성함수를 미분하는 방법인데, 합성함수의 변화 값이 그 안에 구성함수로써 존재하는 다양한 변수(다변량 함수의 다양한 변수)들이 어떻게 변하게 되는지 추적할수 있다.

![KakaoTalk_20240526_163602832](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/d29193dc-a26e-4a2b-b477-891173c8fc93)

우리는 이를 이용하여, 즉 gradient값을 이용하여 극소값을 찾는 최적화 문제를 풀 수 있다.

![최적화 문제 예시](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/88fb2d3a-a69c-4c3d-b860-188f1c866aab)



5. DNN의 장단점
장점:
(1)다층 구조를 통해 복잡한 비선형 문제를 효과적으로 해결할 수 있다.
(2)일반화에 강한 면을 보인다.
(3)분류, 예측 문제 모두에 적용이 가능하며 활용성이 높다.

단점:
(1) 계산량이 많고 복잡하다
(2) 많은 하이퍼 파라미터들이 존재하기 때문에 조정 과정은 복잡하고 시간이 많이 소요된다.

-Explaining features (if any)
1. Binary cross entropy
최적화 문제에 사용될 loss funtion은 다양한 것들이 사용되지만, 이중 우리가 사용할 loss function은 
Binary Cross Entropy(BCE)이다. BCE는 이진화된 label을 가진 데이터에 사용되는 손실함수로, 최적화를 통해 두 라벨에 대한 베르누이 확률 분포의 근사를 수행하게 만든다.

![KakaoTalk_20240526_164747044](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/43ed4952-64d3-46d2-b76f-e354cb795121)

2. 활성화함수
활성화함수란 다층 구조의 신경망에서 주로 사용되는 함수로, 인공신경망의 각 노드에서 입력받은 신호를 학습에 이용할 수 있게 출력 신호로 처리한다. 비선형성을 도입하여 딥러닝 모델이 복잡한 패턴을 학습할 수 있게 하고, 효율적인 정보전달이 가능하게 하며 노드의 활성화 여부를 결정한다. 아래 이미지는 다양한 활성화 함수의 예시이다.

![KakaoTalk_20240526_164747044_01](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/3e66eaf5-bc43-4160-91af-15e4484e2088)


IV. Evaluation & Analysis-Graphs, tables, any statistics (if any)


![KakaoTalk_20240616_104311355](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/41aa17c7-fccb-4fc8-a81d-96a776e0610e)

data에 대한 information이다. 모두 11개의 독립변수가 존재하며 299개의 데이터가 존재한다. null 값은 존재하지 않고 데이터 타입이 float와 int로 존재함으로 따로 vector화할 필요는 없다.

![KakaoTalk_20240616_104528371](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/6f0e7d3f-8633-4ed9-8a9a-7315f601ef40)

데이터의 고유값 갯수이다. 표를 보면 anaemia, diabetes, high_blood_pressure, sex, smoking은 binary 변수이며, 우리의 target 변수인 DEATH_EVENT 역시 binary 변수이다.

![KakaoTalk_20240616_104754013](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/0efdd367-1cf3-4dcc-a53a-d71071e54b70)

다음은 데이터의 상위 5개의 변수를 보여준 표이다.

![KakaoTalk_20240616_103254882](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/7433d075-8d5b-4c75-b08b-e6c707dc261a)

각 변수와 death  간의 상관계수에 대한 히트맵이다. 표를 보면 성별과 다른 변수들에 비해 상대적으로 높은 선형관계를 가짐을 알 수 있다.

V. Conclusion: Discussion
