# 심장병 예측 모델 개발 프로젝트

![143775_149126_4441](https://github.com/SeokcheonMoon/heart_disease_predictions/assets/151099231/cdd265c9-2075-45a8-ab0a-36ba640b8a6d)

### Overview
- 심혈관질환 사건은 1990년에 2억 7100만 건에 달했지만 2019년에는 5억 2300만 건으로 30년간 약 2배로 뛰었다. 

- 심혈관질환에 의해 사망한 환자도 1990년에 1210만 명에서 2019년 1860만 명으로 꾸준히 증가했다. 

- 출처 : [메디칼업저버](http://www.monews.co.kr/news/articleView.html?idxno=300602)

### 프로젝트 목적

- 인간의 생체활동에 관한 dataset을 이용하여 심장질환 여부를 예측할 수 있는 모델 개발 

- 예측 모델 개발 시 이후 입력 데이터에 대하여 위험도를 인지할 수 있는 지표가 될 수 있음.

### 프로젝트 기간

- 2024.11.20 ~ 2024.11.26

## 주요 기술
|Name|Description|Detail|
|--|--|--|
|Python|사용 프로그래밍 언어|Pandas, Matplotlib, Seaborn, Scikit-learn 등|
|Jupyter|웹 프레임워크|Jupyterlab 사용|
|Docker|협업 툴|개발 환경 공유|

## Process

|Stage|Activity|Date|Comment|Code Link|
|--|--|--|--|--|
|1|Docker 설치|2024.11.20|분석 환경 구성|[Docker 설치](https://github.com/SeokcheonMoon/heart_disease_predictions/blob/main/Docker/docker-compose.yml)|
|2|EDA|2024.11.22|데이터 시각화, 컬럼별 심장병 유무 연관성 파악|[데이터 시각화](https://github.com/SeokcheonMoon/heart_disease_predictions/blob/main/data_analysis/DA/analysis_visualization.ipynb)|
|3|CDA|2024.11.23|가설 생성 및 검증|[가설 검증](https://github.com/SeokcheonMoon/heart_disease_predictions/blob/main/data_analysis/DA/analysis_hypothesis.ipynb)|
|4|분류 모델 생성|2024.11.25|모델 학습 및 테스트|[모델 생성](https://github.com/SeokcheonMoon/heart_disease_predictions/blob/main/data_analysis/ML/modeling_prediction_basic.ipynb)|
|5|분류 모델 향상|2024.11.25|클래스 불균형 처리|[오버샘플링 선정](https://github.com/SeokcheonMoon/heart_disease_predictions/blob/main/data_analysis/ML/oversampling_xgboost.ipynb)|
|||2024.11.25|임계값 조정 및 하이퍼파라미터 튜닝|[튜닝](https://github.com/SeokcheonMoon/heart_disease_predictions/blob/main/data_analysis/ML/tuning_oversampling_xgboost.ipynb)|
|||2024.11.25|훈련데이터량 증가|[훈련데이터량 증가](https://github.com/SeokcheonMoon/heart_disease_predictions/blob/main/data_analysis/ML/modifying_training_percent.ipynb)|
|6|향상 방안 모색|2024.11.26 ~ |||

## 분석결과

### (1) 데이터 시각화
![image](https://github.com/user-attachments/assets/52f81237-ecea-4546-80f6-13d1c2eb160f)
![image](https://github.com/user-attachments/assets/546e27fd-90c7-4f3d-be9c-b30277973795)

=> 위와 같이 각 컬럼들에 대해 시각화 진행하였음.

### (2) 통계적 검증
![image](https://github.com/user-attachments/assets/4893ed4d-4bd7-481a-aaab-984989ced1f0)

=> 위와 같이 각 컬럼마다 카이제곱을 이용한 연관성을 분석함.

- 분석 결과 : 정신적 질환 정도를 제외한 나머지 변수들이 모두 유의미함.
- 방향성 제시 : 각 변수들을 이용하여 심장병을 예측하는 모델 개발

## 머신러닝 모델 개발

### ML process

1. 초기 접근
    - 수치형 데이터를 범주화한 뒤 레이블 인코딩 처리 이후 머신러닝 학습
    - 한계 : 수치형 데이터의 연속된 특성을 잃어버릴 수 있음.
    - 가장 성능이 좋은 XGBoost 선정 후 튜닝 및 재학습

2. 2차 접근
    - 초기와 같이 4가지 모델 학습(위와 동일)
    - 수치형 데이터는 그대로 학습에 진행
    - 기존과 비슷한 성능을 보임.

### ML result(진행중)

![image](https://github.com/user-attachments/assets/6fe3a7b2-bd5e-4440-be77-f204e1740d91)
![image](https://github.com/user-attachments/assets/70fabee4-d6b3-43e6-b298-ca95d214bc6d)

=> 심장병 있음(1)에 대한 정밀도 및 재현율이 떨어지는 것으로 보임.

## Reference
- dataset 출처 : [Kaggle](https://www.kaggle.com/datasets/aqleemkhan/heart-disease-2020/data)