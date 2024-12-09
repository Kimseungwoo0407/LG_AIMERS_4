# 고객 전환율 예측 프로젝트

이 프로젝트는 고객 데이터를 기반으로 비즈니스 결과를 예측하는 머신러닝 모델을 개발하는 데 목적이 있습니다. 결측치 처리, 특성 엔지니어링, 모델 학습 등의 과정을 포함하여 예측 성능을 개선하는 것을 목표로 합니다.

---

## 📁 파일 설명

- **`train.csv`**: 모델 학습을 위한 데이터셋.
- **`submission.csv`**: 예측 및 제출을 위한 테스트 데이터셋.

---

## 🛠️ 주요 구성 요소

### 1. 데이터 로딩 및 초기 설정
- `pandas`를 사용해 학습 데이터(`train.csv`)와 테스트 데이터(`submission.csv`)를 불러옵니다.
- `response_corporate_1`과 같은 파생 특성을 생성합니다.

### 2. 매핑 및 변환
- **`response_corporate`**:
  - 기업 코드를 국가 이름으로 매핑하고, 국가에 따라 대륙 정보를 추가합니다.
- **결측값 처리**:
  - 범주형과 수치형 데이터의 결측값을 그룹 통계(중앙값, 최빈값 등)를 기반으로 채웁니다.
  - `product_category`, `business_area`와 같은 변수의 결측값을 그룹별로 가장 빈번하게 나타나는 값으로 대체합니다.

### 3. 특성 엔지니어링
- **빈도 특성**:
  - `customer_idx_freq`, `lead_owner_freq`, `response_corporate_freq`와 같이 값의 빈도를 나타내는 특성을 추가합니다.
- **비율 계산**:
  - `historical_conversion_rate_per_customer`와 같은 비율 기반 특성을 생성하여 예측 성능을 강화합니다.

### 4. 데이터 통합
- 학습 데이터와 테스트 데이터를 통합하여 일관된 전처리를 진행합니다.
- 결측값은 그룹 통계를 활용해 채워 데이터 손실을 최소화합니다.

---

## 🚀 실행 방법

### 1. 필수 라이브러리 설치
다음 Python 패키지가 설치되어 있어야 합니다:
```bash
pip install pandas numpy scikit-learn tqdm gensim lightgbm

. 데이터 준비
train.csv와 submission.csv 파일을 프로젝트의 루트 디렉터리에 배치합니다.

3. 스크립트 실행
메인 Python 스크립트를 실행합니다:

bash
코드 복사
python main.py
📦 사용된 라이브러리
pandas: 데이터 조작 및 정리.
numpy: 수치 계산 및 결측값 처리.
scikit-learn: 머신러닝 모델 학습 및 평가.
gensim: 고급 자연어 처리.
lightgbm: 고성능 그래디언트 부스팅 알고리즘.
🔧 향후 개선 사항
하이퍼파라미터 튜닝:
Grid Search 또는 Bayesian Optimization을 사용해 모델 파라미터 최적화.
특성 확장:
외부 데이터를 활용하여 더욱 풍부한 특성 생성.
모델 평가 개선:
F1-score, ROC-AUC와 같은 추가 지표를 활용해 더 신뢰성 있는 평가 수행.
📞 문의
문의사항 또는 피드백이 있으시면 email@example.com으로 연락 부탁드립니다.
