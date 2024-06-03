# 심장병 예측 모델 개발 프로젝트

## Overview
- 심혈관질환 사건은 1990년에 2억 7100만 건에 달했지만 2019년에는 5억 2300만 건으로 30년간 약 2배로 뛰었다. 

- 심혈관질환에 의해 사망한 환자도 1990년에 1210만 명에서 2019년 1860만 명으로 꾸준히 증가했다. 

- 출처 : [메디칼업저버](http://www.monews.co.kr/news/articleView.html?idxno=300602)

## 프로젝트 목적

- 인간의 생체활동에 관한 dataset을 이용하여 심장질환 여부를 예측할 수 있는 모델 개발 

- 예측 모델 개발 시 이후 입력 데이터에 대하여 위험도를 인지할 수 있는 지표가 될 수 있음.

## Dataset Description

|No.|Data|Description|Type|
|--|--|--|--|
|1|HeartDisease|심장 질환 유무|Categorical|
|2|BMI|BMI 수치|Numerical|
|3|Smoking|흡연 여부|Categorical|
|4|AlcoholDrinking|음주 여부|Categorical|
|5|Stroke|뇌졸증 여부|Categorical|
|6|PhysicalHealth|한 달 내 신체적으로 건강하지 않은 일수|Numerical|
|7|MentalHealth|한 달 내 정신적으로 건강하지 않은 일수|Numerical|
|8|DiffWalking|보행 시 어려움 여부|Categorical|
|9|Sex|성별|Categorical|
|10|AgeCategory|연령대|Categorical|
|11|Race|인종|Categorical|
|12|Diabetic|당뇨병 여부|Categorical|
|13|PhysicalActivity|한 달 내 신체활동 여부|Categorical|
|14|GenHealth|주관적인 건강 상태|Categorical|
|15|Sleeptime|1일 평균 수면 시간|Numerical|
|16|Asthma|천식 여부|Categorical|
|17|KidneyDisease|신장 질환 여부|Categorical|
|18|SkinCancer|피부암 여부|Categorical|

## 주요 기술
|Name|Description|Where to Use|
|--|--|--|
|Python|기본 프로그래밍 언어|데이터 분석|
|Jupyter|분석 환경 세팅|데이터 분석 및 모델 개발|
|Docker|협업 툴|개발 환경 공유|

## 모델 성능 확인

### 평가 지표
    - 0(심장병 없음)에 대한 (Precision 결과 / Recall 결과)
    - 1(심장병 있음)에 대한 (Precision 결과 / Recall 결과)

### (1) 초기 분류 모델
    1. Logistic Regression :  (0.92 / 0.99) , (0.52 / 0.10)
    2. RandomForrest : (0.92 / 0.98) , (0.36 / 0.12)
    3. Kneighbors : (0.92 / 0.98) , (0.32 / 0.08)
    4. Support Vector Machine : (0.92 / 1.00) , (0.00 / 0.00)
=> 1(심장병 있음)에 대한 예측 성능이 전체적으로 낮은 것을 확인.

### (2) Hyper parameter
    Logistic Regression : (0.92 / 0.99) , (0.53 / 0.11)
=> 모델 튜닝 이후 데이터 불균형을 위한 Sampling 고려.

### (3) OverSampling
    1. SMOTE : (0.75 / 0.70) , (0.72 / 0.77)
    2. ADASYN : (0.74 / 0.69) , (0.71 / 0.75)
    3. RandomOverSampler : (0.75 / 0.74) , (0.75 / 0.76)
=> 대체적으로 OverSampling에서 준수한 예측 성능을 보임.

### (4) UnderSampling
    1. RandomUnderSampler : (0.75 / 0.74) , (0.75 / 0.75)
    2. TomekLinks : (0.92 / 0.99) , (0.56 / 0.13)
    3. EditedNearestNeighbours : (0.92 / 0.98) , (0.62 / 0.27)
=> RandomUnderSampler를 제외한 나머지 두 모델은 예측 성능이 떨어지는 것을 확인.

### 결과 1 : 1(심장병 있음)에 대한 예측 성능이 가장 높은 로지스틱 회귀를 선정.
### 결과 2 : OverSampling 중 가장 높은 성능(77%)을 보이는 RandomOverSampler 채택.

## Reference
- dataset 출처 : [Kaggle](https://www.kaggle.com/datasets/aqleemkhan/heart-disease-2020/data)