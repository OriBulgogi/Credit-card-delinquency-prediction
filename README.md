# Credit-card-delinquency-prediction
DACON 신용카드 사용자 연체 예측 AI 경진대회 ( model : stacking ensemble )
대회링크 : https://dacon.io/competitions/official/235713/overview/description
대회의 정의와 데이터 각각의 설명은 해당 링크로 확인 

#### 소스 목차
![image](https://user-images.githubusercontent.com/81247213/147642773-ae0249ae-7f89-41b3-b67b-6867a52e0539.png)

####  EDA
소스코드에 EDA는 제외되어있습니다
이외 fearture engineering, learning model, parameter tuning 은 주석에 포함

  - child_NUM 의 극빈값의 이상치 제거
  ![image](https://user-images.githubusercontent.com/81247213/147640762-f443b0e6-8723-4489-b78c-ff5dde2b1651.png)
  
  - target 인 Credit과 의존도 분석에서 차이를 보이는 feature를 발굴
    - 수입분류/ Credit
    - 가족구성형태/ Credit
    
   ![image](https://user-images.githubusercontent.com/81247213/147640908-c3bd083a-15f6-4417-b855-c05c53d7a5e3.png)
  
  - 직업 분류에 따른 credit
    - 좌 그래프 (상대 수치) : 직업의 분류에 따라 credit의 비율이 유의미한 차이보임
    - 우 그래프 (절대 수치) : 좌그래프의 차이는 IT staff와 같이 극빈값을 가지는 필드(모수의 불균형)이 있으므로 가중치를 부여하기에 무리가 있음
  
  ![image](https://user-images.githubusercontent.com/81247213/147641372-a2ca1000-106d-487c-b4d1-a92d77276600.png)

  - 변수간 상관도 heatmap : child num <-> Family size 간의 상관도가 높다
  
  ![image](https://user-images.githubusercontent.com/81247213/147641472-0b8653c7-616b-498d-ba9e-20ce3b1d89e4.png)

  - 평준화 : 수치 데이터들 중 치우친 변수를 탐색하고 평준화를 적용한다.
  
   ![image](https://user-images.githubusercontent.com/81247213/147641645-41e84de0-1848-42a1-afc4-0c3078195365.png)

  - 중복 데이터가 있다는 의심과 가정
    1. 모든 값이 중복되는 데이터가 적지 않았다 (1634)
    2. 단순히 중복데이터를 삭제 하였을때 현저히 성능저하
    3. 같은 사람이 "발급일"만 다르다
    4. 또한 Credit이 다른경우, 각 신용카드 마드 상환률이 달랏다는 가정
    
    ![image](https://user-images.githubusercontent.com/81247213/147641898-432de69c-c9b9-4fdf-b523-2b83a7a3b727.png)

#### reference
> https://www.kaggle.com/arthurtok/introduction-to-ensembling-stacking-in-python
> https://www.koreascience.or.kr/article/JAKO201206735658112.pdf
> https://dacon.io/competitions/official/235713/codeshare/2594?page=3&dtype=recent
> 

