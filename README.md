# Rocketpunch project

## 분석 목적
등록되는 계정의 스팸 여부 판단

## 데이터
스팸 계정 369개, 정상 계정 69297개로 전체의 0.5%가 스팸인 unbalanced 데이터
전체 데이터를 6 : 2 : 2로 나누어 training, validation, test로 이용

### 변수 전처리
#### blog, cover, employee_count, exit_type, found_date, github, googleplus

#### can_military_service
범주가 3개인 categorical 변수 -> one-hot encoding

#### description
training 데이터의 스팸 계정에서 사용 된 단어를 몇 개 포함하고 있는지 나타내는 새로운 변수 '변수이름_spam' 추가
training 데이터의 정상 계정에서 사용 된 단어를 몇 개 포함하고 있는지 나타내는 새로운 변수 '변수이름_ham' 추가

#### homepage
사용 된 글자수를 나타내는 새로운 변수 'homepage_n' 추가

## 분석 방법
Random forest 이용
1. Hyperparameter tuning이 쉬움
2. Computing time이 짧음
3. Able to perform as well as more complex model
