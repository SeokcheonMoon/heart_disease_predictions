# 심장병 예측 모델 개발 프로젝트

![143775_149126_4441](https://github.com/SeokcheonMoon/heart_disease_predictions/assets/151099231/cdd265c9-2075-45a8-ab0a-36ba640b8a6d)

## Overview
- 심혈관질환 사건은 1990년에 2억 7100만 건에 달했지만 2019년에는 5억 2300만 건으로 30년간 약 2배로 뛰었다. 

- 심혈관질환에 의해 사망한 환자도 1990년에 1210만 명에서 2019년 1860만 명으로 꾸준히 증가했다. 

- 출처 : [메디칼업저버](http://www.monews.co.kr/news/articleView.html?idxno=300602)

## 프로젝트 목적

- 인간의 생체활동에 관한 dataset을 이용하여 심장질환 여부를 예측할 수 있는 모델 개발 

- 예측 모델 개발 시 이후 입력 데이터에 대하여 위험도를 인지할 수 있는 지표가 될 수 있음.

## 프로젝트 기간

- 2024.05.30 ~ 2024.06.10

## 주요 기술
|Name|Description|Where to Use|
|--|--|--|
|Python|기본 프로그래밍 언어|데이터 분석|
|Jupyter|분석 환경 세팅|데이터 분석 및 모델 개발|
|Docker|협업 툴|개발 환경 공유|

## 프로젝트 단계
|Stage|Description|Source|
|--|--|--|
|Step 1|Docker 설치 및 분석 환경 세팅|[Docker 설치](https://github.com/SeokcheonMoon/heart_disease_predictions/blob/main/Docker/docker-compose.yml)|
|Step 2|데이터셋 확인, 가설 생성 후 상관관계 파악|[데이터 분석](https://github.com/SeokcheonMoon/heart_disease_predictions/blob/main/data_analysis/DA/data_analystic_health.ipynb)|
|Step 3|분류 모델 생성 및 모델 선정|[분류 모델 생성](https://github.com/SeokcheonMoon/heart_disease_predictions/blob/main/data_analysis/ML/classification_basic.ipynb)|
|Step 4|하이퍼 파라미터 및 샘플링 적용|[분류 모델 성능 향상](https://github.com/SeokcheonMoon/heart_disease_predictions/blob/main/data_analysis/ML/classification_oversampling_RandomOverSampler.ipynb)|

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

## 느낀점
- 과정이 미숙하지만 스스로 데이터 셋을 가져와 데이터 분석을 통해 가설 생성 후 상관관계를 파악하고 분류 모델 생성까지 하는 첫번째 개인 프로젝트라는 것에 의미를 둠.
- 모델 개발 과정에서 다른 모델들의 하이퍼 파라미터를 적용시킨 후 모델 선정을 하는 것은 어땠을까 생각함.

## Reference
- dataset 출처 : [Kaggle](https://www.kaggle.com/datasets/aqleemkhan/heart-disease-2020/data)