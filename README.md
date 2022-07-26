# SSU-데이터톤-2022

도서관 출입 데이터를 활용한 도서관 혼잡도 분석

## 기존 아이디어
숭실대 학생들을 대상으로 한 설문조사에서 ‘도서관에서 제공해 주었으면 하는 서비스‘로 **‘도서관 혼잡도 제공 서비스**가 가장 큰 비율을 차지함
학생들의 니즈에 따라, 혼잡도를 2가지 방식으로 제안하고자 함
1) **도서관의 입·출입 데이터를 활용하여 지난 요일과 시간대별 혼잡도 제공**
2) 도서관의 실시간 혼잡도 제공

![image](https://user-images.githubusercontent.com/77826531/180228515-8488ee5e-f203-4d17-b960-f22e949f71c6.png)

## 1,2 주차 진행
학생들의 도서관 입·출입 데이터를 요일별로 구분  
-> 데이터_도서관출입.csv 파일의 출입일시의 출력형태에 요일을 추가
![image](https://user-images.githubusercontent.com/77826531/180229784-08c072b6-d969-4c2f-9677-e78d15ade256.png)

## 3주차 진행
전체 데이터에서 요일별 출입 횟수를 추출한 DataFrame을 통해 요일별 혼잡도를 그래프로 시각화  
![image](https://user-images.githubusercontent.com/77826531/180230253-ef826d26-3e23-4550-945d-e30706fd9e85.png)

월별+요일별 도서관 혼잡도를 그래프로 시각화
![image](https://user-images.githubusercontent.com/77826531/180231033-82384aa7-a42a-4bd1-8f31-f637f364c84a.png)  
 
 월별 도서관 혼잡도 비교  
 ![image](https://user-images.githubusercontent.com/77826531/180231171-55f8e07d-2d4d-460a-8099-bc0527126247.png)
- 3주차에 진행했던 데이터 분석에서는  3, 4, 5, 6월의 출입일시만 불러와지는 것을 확인

## 4주차
- 잘못되었던 점
1) 제공받은 데이터는 약 80만개였지만, 3주차까지의 분석이 그것의 일부인 10만개였음  
2) csv파일 의 수정과 저장 -> 출입일시에 요일을 추가했음  
- 개선점  
데이터 파일에 직접적으로 요일을 추가하는 것이 아니라, csv에서 제공받은 출입입시를 훼손하지 않고 파이썬 datetime 모듈로 요일을 구함  

전체 데이터를 대상으로 한 요일별 도서관 혼잡도
![image](https://user-images.githubusercontent.com/77826531/180232404-7bfbd7de-a159-4e73-a459-c195189d2cce.png)
- 요일별로 도서관 출입 횟수를 구하기 위해 출입일시에서 날짜만을 가져온 새로운 데이터 프레임을 생성  
- 각 요일에 해당하는 출입일시만 추출하여 요일별로 입·출입의 횟수를 구함  
- 💡결과 
  - ‘월 – 화 – 수 – 목 – 금 – 토 – 일’ 순으로 도서관의 입출입 횟수가 잦음을 알 수 있음. 주말보다 평일의 이용이 약 4배 이상 많았음. 
  - 전체 데이터를 대상으로 한 요일별 데이터의 양이 너무 방대하여 유용한 정보를 제공하지 못한다고 판단하였기에 월별 + 요일별 데이터를 분석하고자 함
  
월별로 요일별 도서관 출입 횟수를 그래프로 시각화(1월 ~ 12월)  
![image](https://user-images.githubusercontent.com/77826531/180233661-7f0a8d89-722d-491e-8998-5997a7a7bad0.png)

월별 출입횟수를 그래프로 시각화
![image](https://user-images.githubusercontent.com/77826531/180234027-3a113767-5083-4cd1-ba4b-7ba884d019c4.png)
- 💡결과
  - 월별 데이터를 바탕으로 요일별 혼잡도를 확인했을 때, 가장 혼잡한 요일은 월요일인 경우가 가장 많았음. 하지만 매 달마다 조금씩 달랐기 때문에 규칙을 찾기는 어려움.
  - 월별 출입횟수 그래프를 통해 학기중인 기간과 방학기간의 도서관 이용자의 차이가 크다는 것을 알 수 있었음
학기중에서도 중간고사와 기말고사 기간인 4,6월 10,12월이 더 혼잡했음.
  - 따라서 도서관이 항상 일정한 혼잡도를 유지하는 것이 아니라 요일이나 시험기간과 같은 특정기간에 따라 혼잡도에 많은 차이를 보이는 것으로 파악됨. 그러므로 도서관 혼잡도 서비스 제공은 학생들의 편의를 더해줄 수 있음.


각 요일별로 어떤 시간이 가장 혼잡했는지 분석
- 시간단위로 (입구-출구) 횟수를 구하여 혼잡도를 계산하고자 함
- 도서관 운영시간 6시 ~ 23시
- (입구-출구) > 0 : 나가는 사람보다 들어오는 사람이 많기에 혼잡
- (입구-출구) < 0 : 나가는 사람이 들어오는 사람보다 많기 때문에 한적함

![image](https://user-images.githubusercontent.com/77826531/180234742-24d877e3-1659-4d1f-8d6e-e3ea6e53e2ce.png)

- 💡결과
  - 가장 혼잡한 시간은 평일은 12~13시였고 주말은 13~14시로 나타남  
  
## 5주차
4주차까지의 분석을 통해, 도서관 혼잡도 예측 서비스를 구현하고자 함
- 시간 단위로 (입구-출구) 횟수를 축적 시켜, 어떤 시간에 도서관에 사람이 가장 많이 군집해 있는지에 대한 정확도를 높이고자 함
- 일자별로 시간 단위 도서관의 사람 수를 리스트(list_accumulate)에 저장

![image](https://user-images.githubusercontent.com/77826531/180235039-a5148bb5-0ae9-40bb-a8ef-8e8b53d56852.png)

- most_crowed_time_list는 과거(이전날)의 축적 데이터를 통해 가장 혼잡한 시간을 예측한 리스트
- 가정) 이 전날에 가장 혼잡했던 시간이 그 다음날에도 가장 혼잡할 것이라고 예측

![image](https://user-images.githubusercontent.com/77826531/180235180-aa0a8fb6-9cfd-4bde-bb46-aa5abde850ec.png)

![image](https://user-images.githubusercontent.com/77826531/180235213-416cdefa-60f7-4ce6-901f-c4ed3511b7e3.png)

- 대체적으로 13,14,15,16시가 가장 혼잡할 것 같은 시간으로 결과가 도출됨
- 그 중에서도 15시가 가장 혼잡

![image](https://user-images.githubusercontent.com/77826531/180235291-39034e7f-7cdc-4204-b9e2-a6a57352ba64.png)

