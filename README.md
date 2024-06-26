# predict-survival-of-patients-with-heart-failure
Title: predict survival of patients with heart failure

Members: 김예원(건축학과, yeawon0515@hanyang.ac.kr)  신승국(수리데이터사이언스학과, tlstmdrnr135@naver.com)  장위신(기계공학과,weixin0713@hanyang.ac.kr）
         
I. Proposal 

심부전이란 심장의 구조적 또는 기능적 이상으로 인해 심장이 혈액을 받아들이는 이완 기능이나 짜내는 수축 기능이 감소하여 신체 조직에 필요한 혈액을 제대로 공급하지 못해 발생하는 질환군을 말한다. 발생 원인은 스트레스, 식습관, 음주 등 매우 다양하게 나타나며 바쁜 사회를 살아가는 현대인들에게 발생률이 점점 증가하고 있다. 또한 이 질환은 생명과 직결되는 중요한 문제임으로 이에 대한 예측은 오늘날 매우 중요한 과제라고 할 수 있다. 
딥러닝은 주어진 데이터를 토대로 예측을 수행하는 매우 강력한 수단 중 하나로, 많은 사람들에게 관심을 받으며 빠른 속도로 변화하고 있다. 또한 다양한 산업과 직군 속에서 활용 및 가치를 창출하고 있으며 따라서 이에대한 역량을 갖추는 것은 매우 중요한 일 중 하나이다. 우리는 DNN 모델의 구조를 파악하고 심부전에 의한 사망 여부 예측을 통해 간단한 문제를 해결한 후 다른 여러 머신러닝 기법들과 비교를 통해 딥러닝의 특성을 파악함으로써 이러한 역량을 갖출수 있고자 한다.



II. Datasets

출처: https://www.kaggle.com/datasets/rabieelkharoua/predict-survival-of-patients-with-heart-failure

변수 설명:
    age 나이
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

1. ANN(인공신경망)이란?
인공신경망(ANN)이란 동물 뇌의 신경망을 모방해 만든 알고리즘으로, 뉴런을 모방한 노드들이 연결되어 있는 형태이다. 일반적으로 각각 한 개의 입력층과 출력층, 은닉층을 가진다.


2. DNN이란?
가장 기본적인 형태인 ANN을 응용하기 위하여 은닉층의 수를 2개 이상으로 늘린 신경망 구조를 가진 모델인 DNN(Deep Neural Network)을 이용한다.

![DNN i](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/74c5fffd-904b-4780-9dc7-c88548cfb778)


3. DNN의 수학적 베이스

DNN은 은닉층의 수, 노드의 수에 따라 많은 bias과 weight를 가지게 되며 weight의 경우 각 레이어의 노드의 곱, bias은 각 레이어의 노드의 합만큼의 개개수를 가지게 된다. 이들은 chain rule을 이용하여 loss 값을 줄이는 방향으로 학습을 진행하여 결과적으로 들어오는 변수에따라 weight와 bias가 비선형적으로 변하게 된다.
chain rule은 합성함수를 미분하는 방법인데, 합성함수의 변화 값이 그 안에 구성함수로써 존재하는 다양한 변수(다변량 함수의 다양한 변수)들이 어떻게 변하게 되는지 추적할수 있다.

![KakaoTalk_20240526_163602832](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/d29193dc-a26e-4a2b-b477-891173c8fc93)

우리는 이를 이용하여, 즉 gradient값을 이용하여 극솟값을 찾는 최적화 문제를 풀 수 있다.

![최적화 문제 예시](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/88fb2d3a-a69c-4c3d-b860-188f1c866aab)



4. DNN의 장단점

장점:

(1)다층 구조를 통해 복잡한 비선형 문제를 효과적으로 해결할 수 있다.

(2)일반화에 강한 면을 보인다.

(3)분류, 예측 문제 모두에 적용이 가능하며 활용성이 높다.

단점:

(1) 계산량이 많고 복잡하다

(2) 많은 하이퍼 파라미터들이 존재하기 때문에 조정 과정은 복잡하고 시간이 많이 소요된다.



5. Binary cross entropy
최적화 문제에 사용될 loss funtion은 다양한 것들이 사용되지만, 이중 우리가 사용할 loss function은 Binary Cross Entropy(BCE)이다. BCE는 이진화된 label을 가진 데이터에 사용되는 손실함수로, 최적화를 통해 두 라벨에 대한 베르누이 확률 분포의 근사를 수행하게 만든다.

![KakaoTalk_20240526_164747044](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/43ed4952-64d3-46d2-b76f-e354cb795121)

6. 활성화함수
활성화함수란 다층 구조의 신경망에서 주로 사용되는 함수로, 인공신경망의 각 노드에서 입력받은 신호를 학습에 이용할 수 있게 출력 신호로 처리한다. 비선형성을 도입하여 딥러닝 모델이 복잡한 패턴을 학습할 수 있게 하고, 효율적인 정보전달이 가능하게 하며 노드의 활성화 여부를 결정한다. 아래 이미지는 다양한 활성화 함수의 예시이다.

![KakaoTalk_20240526_164747044_01](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/3e66eaf5-bc43-4160-91af-15e4484e2088)



IV. Evaluation & Analysis-Graphs, tables, any statistics (if any)


![KakaoTalk_20240616_104311355](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/41aa17c7-fccb-4fc8-a81d-96a776e0610e)

data에 대한 information이다. 모두 11개의 독립변수가 존재하며 299개의 데이터가 존재한다. null 값은 존재하지 않고 데이터 타입이 float와 int로 존재함으로 따로 임베딩할 필요는 없다.

![KakaoTalk_20240616_104528371](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/6f0e7d3f-8633-4ed9-8a9a-7315f601ef40)

데이터의 고유값 개수이다. 표를 보면 anaemia, diabetes, high_blood_pressure, sex, smoking은 binary 변수이며, 우리의 target 변수인 DEATH_EVENT 역시 binary 변수이다.

![KakaoTalk_20240616_104754013](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/0efdd367-1cf3-4dcc-a53a-d71071e54b70)

다음은 데이터의 상위 5개의 변수를 보여준 표이다.

![KakaoTalk_20240616_103254882](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/7433d075-8d5b-4c75-b08b-e6c707dc261a)

각 변수와 death 간의 상관계수에 대한 히트맵이다. 표를 보면 다른 변수들에 비해 성별과 상대적으로 높은 선형관계를 가짐을 알 수 있다.

![KakaoTalk_20240616_105724555](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/4d7e364a-dcf2-45b6-ac01-17406ac076b6)

종속변수와 독립변수를 분리한다. 이후, 학습량을 줄이고 변수에 대한 영향력을 동일하게 하기위해(KNN 사용시 필요) min-max scaling을 통해 정규화하여 준다. 그리고 20퍼센트 수준으로 train 데이터와 test 데이터를 구성한다.

![KakaoTalk_20240616_110024795](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/4d6db861-037a-4c96-975e-da02b1d5935e)

신경망 구조에 대한 요약이다.
신경망 모델은 총 1개의 입력층, 2개의 은닉층, 그리고 출력층 총 4개의 층으로 구성되어 있으며 활성화 함수로 leakyrelu를 사용하였다. 출력층에는 binary 변수에 대한 예측임으로 시그모이드 함수를 사용하였고 손실함수로 binary cross entropy를 사용하였다.
추가적으로 optimizer는 adam을 사용하였고 learning_rate를 0.0015로 설정하였다.


우리는 결과를 비교해보기 위해 우리가 만든 DNN 모델과 Support Vector Machin(SVM), K-Nearest Neighborhood(KNN), Robust Linear Regression(RLR), RF(Random Forest) 모델을 비교해 보았다. 

![KakaoTalk_20240617_120654112](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/8f36e6b7-a112-4721-9033-69bf85a0f237)

accuracy는 정확도로써 모델이 예측한 값 중 정답의 비율을 나타내며 1에 가까울수록 좋다. 위 표는 test 데이터에 대한 accuracy로 DNN 모델의 Score가 가장 높음을 알 수 있다.

Precision은 모델이 positive라고 예측한 것 중 실제로 positive인 것의 비율이다. 0에서 1 사이의 값을 가지며, 1에 가까울수록 정밀도가 높은 모델이다. 우리는 상식에 접근하여 생각해 보았을 때 살았을 거라고 생각한 예측한 사람 중 사망자가 존재하는 것이 더 문제된다고 판단하였다. 이에 따라 살았을 거라고 생각한 사람 중 진짜로 살아있는 사람에 대한 정확도를 예측하였다.

![KakaoTalk_20240617_120654112_01](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/37669749-a0d4-4c6c-8d0f-a127e3fcc968)

위 표는 정확도에 대한 각 모델의 score이다. 마찬가지로 DNN이 가장 높은 점수를 얻은 것을 볼 수 있다.



V. Conclusion: Discussion

우리는 이번 프로젝트를 통해 인공신경망의 구조와 이에 적용된 수학적 base를 파악할 수 있었으며, 이를 오픈데이터에 적용해 보며 실제 예측또한 수행해 보았다. 그리고 이를 다른 모델들과 비교해보며 그 결과를 분석해보았다. 결론적으로 다른 모델들에 비해 좋은 결과를 얻을 수 있었지만, 코드를 작성하고 하이퍼 파리미터를 조정해 보면서 다른 모델들에 비해 복잡하고 조정해야할 변수가 많아 어려움이 있었다. 따라서 추후에 하이퍼 파라미터를 조정하는 방법에 대해 연구해 보고 이러한 문제점을 해결해 보고자 한다.

김예원(조장): 총괄

신승국: 코드, 발표 영상 제작

장위신: 자료 수집

VI. presentation

https://youtu.be/XrQWpkzby5E

