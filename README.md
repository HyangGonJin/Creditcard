# Creditcard 
+ [신용카드 사용자 연체 예측 AI 경진대회](https://dacon.io/competitions/official/235713/overview/description)

## Feature Engineering
+ 기본 변수
+ `occyp_type`: ['white', 'Laborers', 'Managers','Core staff']로 재범주화

+ Ratio
  + `income_family_ratio`: income_total / family_size
  + `income_birth_ratio`: income_total / days_birth
  + `income_emp_ratio`: income_total / days_employed
  + `birth_emp_ratio`: days_birth / days_employed

+ Group-by Mean & Std
  + `income_type_mean`: 'income_type'별 'income_total'의 평균
  + `income_type_std`: 'income_type'별 'income_total'의 표준편차
  + `edu_type_mean`: 'edu_type'별 'income_total'의 평균
  + `edu_type_std`: 'edu_type'별 'income_total'의 표준편차
  + `house_type_mean`: 'house_type'별 'income_total'의 평균
  + `house_type_std`: 'house_type'별 'income_total'의 표준편차
  + `family_type_mean`: 'family_type'별 'income_total'의 평균
  + `family_type_std`: 'family_type'별 'income_total'의 표준편차
  + `reality_type_mean`: 'reality'별 'income_total'의 평균
  + `reality_type_std`: 'reality'별 'income_total'의 표준편차
  + `email_type_mean`: 'email'별 'income_total'의 평균
  + `email_type_std`: 'email'별 'income_total'의 표준편차
  + `gender_edu_type_mean`: 'gender'와 'edu_type'별 'income_total'의 평균
  + `gender_edu_type_std`: 'gender'와 'edu_type'별 'income_total'의 표준편차

+ 범주형 변수 조합
  + `car+gender`: 'car'+'gender'

+ [rollcake](https://www.dacon.io/competitions/official/235713/codeshare/2526?page=1&dtype=recent)님 코드 참고
  + `birth_month`: df['days_birth']//31)%12
  + `birth_week`: df['days_birth']//7)%4.3
  + `DAYS_EMPLOYED_month`: df['days_employed']//31)%12
  + `DAYS_EMPLOYED_week`: df['days_employed']//7)%4.3
  + `before_EMPLOYED`: df['days_birth'] - df['days_employed']
  + `before_EMPLOYED_month`: df['before_EMPLOYED']//31)%12
  + `before_EMPLOYED_week`: df['before_EMPLOYED']//7)%4.3
  + `DAYS_BIRTH_weekday`: df['days_birth']%7
  + `DAYS_BIRTH_days_in_month`: df['days_birth']%31
  + `DAYS_BIRTH_day`: df['days_birth'])%365 
  + `DAYS_EMPLOYED_weekday`: df['days_employed'])%7 
  + `before_EMPLOYED_weekday`: df['before_EMPLOYED'])%7
  + `before_EMPLOYED_weekday_days_in_month`: df['before_EMPLOYED']%31


## Encoding
+ 'One-hot Encoding'이 'Label Encoding'보다 좋은 성능을 보였음. 
+ `edu_type`: Ordinal encoding
+ 그 외 변수: One-hot encoding


## Cross Validation
+ `KFold`가 `StratifiedKFold`보다 좋은 성능을 보였음. 
+ '10-fold CV'를 이용. 


## 순위
public 67위 private 13위


## 대회 후 Insights
+ **CatBoost**의 성능이 LightGBM, XGBoost보다 더 나은 성능을 보임.
+ 이는 대부분의 feature가 Categorical이었기에 나온 결과로 생각. 


## 참고자료
+ [ds-wook님 Github](https://github.com/ds-wook/PredictCreditCardDelinquency)