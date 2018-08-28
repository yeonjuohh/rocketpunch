# Rocketpunch project

## 분석 목적
등록되는 계정의 스팸 여부 판단

## 데이터
- 스팸 계정 369개, 정상 계정 69297개로 전체의 0.5%가 스팸인 unbalanced 데이터  
- 전체 데이터를 6 : 2 : 2로 나누어 training, validation, test로 이용
- 결측치가 대부분

### 변수 전처리
#### blog, cover, employee_count, exit_type, found_date, github, googleplus, instagram, kakao_story, logo, phone, pinterest, twitter, yellow_id, youtube
NaN 여부를 나타내는 binary 변수로 변환

#### can_military_service
범주가 3개인 categorical 변수 -> one-hot encoding

#### description, name
training 데이터의 스팸 계정에서 사용 된 단어를 몇 개 포함하고 있는지 나타내는 새로운 변수 '변수이름_spam' 추가 -> 표준화  
training 데이터의 정상 계정에서 사용 된 단어를 몇 개 포함하고 있는지 나타내는 새로운 변수 '변수이름_ham' 추가 -> 표준화  

#### homepage
사용 된 글자수를 나타내는 새로운 변수 'homepage_n' 추가

#### overview
사용 된 글자수를 나타내는 새로운 변수 'overview_n' 추가  
training 데이터의 스팸 계정에서 사용 된 단어를 몇 개 포함하고 있는지 나타내는 새로운 변수 'overview_spam' 추가 -> 표준화  
training 데이터의 정상 계정에서 사용 된 단어를 몇 개 포함하고 있는지 나타내는 새로운 변수 'overview_ham' 추가 -> 표준화  

#### permalink
numeric 여부를 나타내는 binary 변수로 변환

#### viewcount
표준화

##### num_nan
각 observation의 NaN 개수를 나타내는 변수 -> 표준화

## 분석 방법
#### Random forest 이용  
1. Hyperparameter tuning이 쉬움  
2. Computing time이 짧음  
3. Able to perform as well as more complex model  

unbalanced 데이터이기 때문에 y = 1(계정은 스팸이다)를 예측하는 것이 중요  
precision과 recall의 가중평균인 f1을 최대로 하는 hyperparameter를 10-folds cross validation를 이용해 찾고자 함  

## 분석 결과

|        | 0     | 1     |
| ------ |:-----:|:-----:|
| 0      | 13325 | 534   |
| 1      | 40    | 34    |

오분류율 = 4.12%
precision = 5.99%
recall = 45.95%
f1 = 10.59%

![alt text](https://github.com/yeonjuohh/rocketpunch/importance.png)
