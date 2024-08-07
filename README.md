# 의료 로봇 섹터 뉴스 데이터 감성 분석을 통한 주식 시장 경향 분석
  
***과연 뉴스 데이터의 긍정-부정 수치를 보고 주식 매도-매수를 해도 될까?*** <br>
***뉴스 데이터와 주식 시장 경향에 유의미한 연관성이 있을까?***


## 🤖 프로젝트 소개
- 본 프로젝트는 뉴스 기사의 정서와 그것이 주가에 미치는 영향을 분석함으로써 시장 행동과 일반적인 투자 전략의 타당성에 대한 더 깊은 이해를 제공하는 것을 목표

## 🧠 구성원 및 역할
|이름|업무|
|:---|:---|
|고선민|- 미국 섹터 Google 웹크롤링 및 전처리 <br> - pipeline을 통한 미국기사 감성분석 <br> - plotly를 통한 주식과 뉴스 데이터의 감성분석 상관관계 및 키워드 시각화|
|강지훈|- 한국 섹터 Naver 웹크롤링 및 데이터 전처리 <br> - yfinance를 통한 기업별 평균 종가 데이터 시각화  <br> - 뉴스 기사량과 주식의 상관관계 분석|
|김주영|- 한국 섹터 Naver 웹크롤링 <br> - 주식 시작 경향 파악 및 데이터 수집 <br> - 종목별 특정 구간에서의 이동평균선 특이점 분석 및 시각화|
|이세형|- Roberta DL 모델을 활용한 자연어 학습 및 감성분석 <br> - DB 구축, 관리, 및 Query 작성 <br> - 뉴스데이터와 주식의 등락에 대한 상관관계 분석|

## 🖥️ 활용 기술
|구분|상세|
|:---|:---|
|개발환경|<img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white" /> |
|IDE| <img src="https://img.shields.io/badge/VSCode-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white" /> <img src="https://img.shields.io/badge/Jupyter-F37626.svg?&style=for-the-badge&logo=Jupyter&logoColor=white" /> <img src="https://img.shields.io/badge/Colab-F9AB00?style=for-the-badge&logo=googlecolab&color=525252" />|
|언어| <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />   |
|EDA 시각화|<img src="https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white" /> <img src="https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white" /> <img src="https://img.shields.io/badge/Plotly-%233F4F75.svg?style=for-the-badge&logo=plotly&logoColor=white" /> <img src="https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black" /> ![yahoo-news (1)](https://github.com/user-attachments/assets/fc51c1aa-3dd5-4732-b0cd-a7d45777c51f)|
|웹 크롤링| <img src="https://img.shields.io/badge/Selenium-43B02A?style=for-the-badge&logo=Selenium&logoColor=white" /> Newspaper3k| 
|DB|<img src="https://img.shields.io/badge/Amazon_RDS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white" /> <img src="https://img.shields.io/badge/MySQL-00000F?style=for-the-badge&logo=mysql&logoColor=white" />|
|협업|<img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" /> <img src="https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white" /> <img src="https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white" /> |

## 📜 웹 크롤링 과정

### 기업 및 사이트 선정
- 한국 및 미국 기업들은 코스피, 나스닥/뉴욕증권거래소에 등재된 의료 로봇 섹터를 기준으로 선정.
- 한국 기사들은 네이버 기사, 미국 기사들은 구글 뉴스를 통해 크롤링 진행.

### 크롤링 데이터 수집 (네이버 한국기사)
- 크롤링 데이터 : **"date", "title", "content", "link"**
- 검색어: "medical robot OR surgical robot", "Intuitive+Surgical", "Stryker+Corporation", "Medtronic", "Globus+Medical", "Asensus+Surgical", "Smith...", "Johnson..."

### 크롤링 데이터 수집 (구글 미국기사)
- 크롤링 데이터 : **"date", "title", "content", "link", keyword"**
- 검색어 : "의료 로봇", "고영", "큐렉소", "미래컴퍼니"


### 수집 데이터 전처리
    - 필요없는 단어 리스트를 생성 후 불용어 처리를 통해 1차 필터링
    - 이후 핵심 키워드 2차 필터링을 통해 해당 단어의 빈출 정도를 파악
    - 빈출도가 높은 순으로 글씨가 크게 나옴
    

### 4.4 직무별 핵심 요구 기술 파악
<div align="left">
    
- **Word Clound 기반 직무별 필요역량 파악**
<img src="https://github.com/AUTO-KKYU/test/assets/118419026/84f6870c-059d-45d9-9bf8-7112e7928ed0" width="800" height="300"/>

- **Word Cloud 기반 빈출 단어**
<img src="https://github.com/AUTO-KKYU/test/assets/118419026/60e6aeb8-f7f1-458d-b029-180a3d69abf2" width="500" height="300"/>

- **직무 별 핵심 키워드**
<img src="https://github.com/AUTO-KKYU/test/assets/118419026/d7da46d6-f5fa-42e3-811b-c8a6811d7d81" width="700" height="500"/>

### 4.5 Folium을 활용한 지역별 직무 분포 시각화
<img src="https://github.com/AUTO-KKYU/test/assets/118419026/098ffbb2-ead2-46d3-b911-36799ed0cef3" width="800" height="300"/>

<figure class="half">
  <a href="link"><img src="https://github.com/donggyu0411/EDA_PROJECT/assets/118419026/6991e47e-5ee7-4d36-ade3-576eb313e484"  width="400" height="200"/ ></a>
  <a href="link"><img src="https://github.com/donggyu0411/EDA_PROJECT/assets/118419026/06d4e91a-7c3d-4ebb-a4be-f54f78f6de3d"  width="400" height="200"/ ></a>
</figure>

## 🗂️ DB 구축
- 채용사이트 DB
    - 기업이름, 고용형태, 연봉, 기업주소, 키워드, 담당업무, 필요역량, 인덱스
- Folium DB
    - 기업이름, 고용형태, 연봉, 기업주소, 키워드, 기업형태, 사원수, 매출액, 인덱스
- 잡플래닛 전체 직무 DB
    - 기업이름, 분야, 평점, 연봉, 2차산업군
- 기업 성장 지표 DB
    - 기업이름, 기업규모, 매출액(21/22/23/ALL), 평균연봉, 자본총계(21/22/23), 순이익(21/22/23), 기준년도, 키워드, 인덱스
<div align="left">

---
## ✅ 취업시장 동향 및 기업 분석

### 6.1 로봇 취업 시장 동향
- **고용 형태 비중**
<div align="left">


- **로봇 기술의 가치**
    - 로봇 기술 시장에서의 가치
        - 로봇기술 사용 유무에 따른 기업 평점 비교 시, 기술 사용 기업이 평점이 높음
    - 로봇 산업군의 연봉
        - 건설업을 제외한 나머지 분야에서 로봇 기술의 가치가 높음
<div align="left">



- **각 분야 별 매출액 및 평균연봉 비교**
    - HW와 SW 모두 사용하는 분야이므로, 상대적으로 매출액 범위와 연봉이 높다
<div align="left">



## 🏁 분석 및 결론

**1. 매출액, 순이익, 자본총계, 성장률, 연봉, 평점 순으로 각 1차 기업 추천리스트 Top10을 선정함**

**2. 뉴스기사 및 기업사이트 등 종합적으로 분석하여 각 키워드별로 기업 추천**
- 자율주행 42dot
- 딥러닝 크래프톤
- 로봇제어 유진로봇
<div align="left">
