# LG_AIMERS_4

README
프로젝트 개요
이 프로젝트는 고객 데이터를 기반으로 비즈니스 성과를 예측하기 위한 머신러닝 모델을 구축하는 데 초점을 맞춥니다.
학습 데이터셋(train.csv)과 테스트 데이터셋(submission.csv)을 사용하여 다양한 결측값 처리, 데이터 변환, 특성 엔지니어링을 수행하고, 이를 통해 모델의 성능을 향상시킵니다.

파일 설명
train.csv: 학습에 사용되는 데이터셋
submission.csv: 테스트 데이터셋으로, 결과 제출을 위한 데이터
주요 코드 구성
1. 데이터 로드 및 초기 설정
학습용(train.csv) 및 테스트용 데이터셋(submission.csv)을 pandas를 사용하여 로드합니다.
일부 데이터 컬럼(예: response_corporate)을 활용해 response_corporate_1와 같은 추가 파생 컬럼을 생성합니다.
2. 데이터 매핑 및 변환
response_corporate 컬럼: 기업 코드와 국가명 간의 매핑을 수행한 뒤 국가명 기반 대륙 정보를 추가로 매핑.
결측값 처리:
그룹별(bant_submit, business_unit)로 결측값을 채움 (예: 중앙값, 최빈값).
범주형 데이터(product_category, business_area)는 그룹별 최빈값으로 대체.
수치형 데이터(ver_win_rate_x, historical_conversion_rate_per_customer)는 평균 또는 중앙값으로 대체.
3. 파생 변수 생성
customer_idx_freq, lead_owner_freq, response_corporate_freq: 특정 컬럼 값의 빈도를 계산하여 새로 생성된 컬럼에 저장.
historical_conversion_rate_per_customer: 고객별 과거 전환율 계산.
4. 데이터 특성 엔지니어링
비율 계산: historical_conversion_rate_per_customer와 같은 비율 데이터를 추가하여 데이터를 보강.
범주형 컬럼의 재구성: customer_country, business_area 등의 컬럼을 그룹화하여 범주형 데이터를 더 세분화.
5. 데이터 결합 및 결측값 처리
학습 데이터와 테스트 데이터에 동일한 결측값 처리 방식을 적용.
그룹화한 데이터를 활용해 결측값을 채움으로써 데이터 손실 최소화.
