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

- 2024.11.20 ~ 진행중

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
|4|머신러닝 분류 모델 생성||||
|5|분류 모델 성능 최적화||||

## 분석 결과


## 머신러닝 모델 개발

## Reference
- dataset 출처 : [Kaggle](https://www.kaggle.com/datasets/aqleemkhan/heart-disease-2020/data)