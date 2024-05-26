# predict-survival-of-patients-with-heart-failure
Title: predict survival of patients with heart failure

Members: 김예원(건축학과, yeawon0515@hanyang.ac.kr)
         신승국(수리데이터사이언스학과, tlstmdrnr135@naver.com)
         
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
ANN(인공신경망)이란?
인공신경망(ANN)이란 동물 뇌의 신경망을 모방해 만든 알고리즘으로, 뉴런을 모방한 노드들이 연결되어 있는 형태이다. 일반적으로 각각 한 개의 입력층과 출력층, 은닉층을 가진다.

![DNN i](https://github.com/kimyeawon/predict-survival-of-patients-with-heart-failure/assets/168324887/27a14b74-d0ba-4f5f-b823-ed975f2f305c)

가장 기본적인 형태인 ANN을 응용하기 위하여 은닉층의 수를 2개 이상으로 늘린 신경망 구조를 가진 모델인 DNN(Deep Neural Network)을 이용한다. DNN은 은닉층의 수, 노드의 수에 따라 많은 bias과 weight를 가지게 되며 weight의 경우 각 레이어의 노드의 곱, bias은 각 레이어의 노드의 합만큼의 갯수를 가지게 된다. 이들은 chain rule을 이용하여 loss 값을 줄이는 방향으로 학습을 진행하여 결과적으로 들어오는 변수에따라 weight와 bias가 비선형적으로 변하게 된다. 여기서 chain rule은 합성함수를 미분하는 방법인데, 합성함수의 변화 값이 그 안에 구성함수로써 존재하는 다양한 변수(다변량 함수의 다양한 변수)들이 어떻게 변하게 되는지 추적할수 있다. 우리는 이를 이용하여, 즉 gradient값을 이용하여 극소값을 찾는 최적화 문제를 풀 수 있다.

장점
(1)다층 구조를 통해 복잡한 비선형 문제를 효과적으로 해결할 수 있다.

(2)일반화에 강한 면을 보인다.

(3)분류, 예측 문제 모두에 적용이 가능하며 활용성이 높다.

단점
(1) 계산량이 많고 복잡하다

(2) 많은 하이퍼 파라미터들이 존재하기 때문에 조정 과정은 복잡하고 시간이 많이 소요된다.



-Explaining your choice of algorithms (methods)
-Explaining features (if any)

IV. Evaluation & Analysis-Graphs, tables, any statistics (if any)

V. Related Work (e.g., existing studies)-Tools, libraries, blogs, or any documentation that you have used to do this project.

VI. Conclusion: Discussion
