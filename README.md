# 수원시 스마트 버스정류장 우선 설치위치 선정  

* **2021 국토도시 데이터 분석과제 입선작**  
* 주최 : **[COMPAS LH](https://compas.lh.or.kr/)**
* 활동 기간 : 21/02/19 - 21/04/16  
* 자세한 분석내용은 **[Link](https://github.com/hrlee113/Suwon-Smart-Bus-Station/blob/main/Results/%EB%B0%9C%ED%91%9C%EC%9E%90%EB%A3%8C_%EC%B2%AD%EC%B6%9C%EC%96%B4%EB%9E%8C.pdf)** 를 통해 확인하실 수 있습니다😄

<table>
  <tr>
    <td align="left"><img src="https://user-images.githubusercontent.com/54944069/114996339-b2376a00-9ed9-11eb-8026-fb8224884324.PNG" width="1000px" alt=""/></a></td>
  </tr>
</table>

## 스마트 버스정류장이란? ##
* 미세먼지 절감과 관련 대기정보를 수집하고 제공하는 것을 목표로 하는 버스정류장입니다.
* **`일반시민의 접근성·편의성이 높은 지역`**, **`대기오염이 심한 지역`** 의 버스정류장을 스마트 버스정류장으로 교체해야 합니다.

## 분석 목표 ##
* 수원시 기존 버스정류장 중, 스마트 버스정류장으로 **우선교체가 필요한 30개의 정류장 위치** 를 도출할 계획입니다.
* 선택된 우선설치 버스정류장별로 **광고 Target층** 을 예측할 계획입니다.

## 주요 특징 ##  

|분석 프로세스
| :-: |
|![국토도시 모델구조](https://user-images.githubusercontent.com/54944069/115835638-72c8ca80-a451-11eb-898a-c18b27a90011.PNG)|

* 버스정류장 고유정보를 이용하여 버스정류장을 특징에 따라 3개의 클러스터로 분류하였습니다. 이 때 사용한 클러스터링 방법은 K-Means Clustering 입니다.  
* 시민들이 버스정류장을 이용하는 시간을 버스정류장 선택에 사용하기 위해, **이용시간** feature를 생성하고 Random Forest Regressor를 이용해 예측했습니다.
* 측정소별 미세먼지·초미세먼지 데이터를 이용하여 버스정류장별 미세먼지·초미세먼지를 예측하기 위해, 보간법을 이용하여 파생변수를 생성했습니다. 그 후 예측에 사용한 모델은 LightGBM입니다.
* 버스정류장별 미세먼지·초미세먼지 데이터를 이용하여 **대기질지수** feature를 생성했습니다.
* **`이용시간`**, **`대기질지수`** 를 통해 **`우선설치 스코어`** 를 생성하고, 이를 기준으로 30개의 스마트 버스정류장 우선설치 위치를 도출했습니다.
* 선택된 정류장별로 성연령별 유동인구 데이터를 이용하여 **광고 Target층**을 도출했습니다. (ex. 1번 정류장 - 20대 여성) 


## 분석 결과 ##
* 이용시간 예측 모델 (Random Forest Regressor) : 모델평균 MAPE 0.06  
* 대기질지수 예측 모델 (LightGBM) : 모델평균 MAPE 0.01
* 우선설치 버스정류장 ·  광고 Target층
<table>
  <tr>
    <td align="left"><img src="https://user-images.githubusercontent.com/54944069/115841483-cdfdbb80-a457-11eb-8ad2-68674e701486.PNG" width="1000px" alt=""/></a></td>
  </tr>
</table>
* 우선설치 정류장 분포지역을 크게 세 지역으로 구분함으로써 지역적 특징 도출
<table>
  <tr>
    <td align="left"><img src="https://user-images.githubusercontent.com/54944069/115841440-bf170900-a457-11eb-96de-ab0ba6888ff6.PNG" width="1000px" alt=""/></a></td>
  </tr>
</table>




