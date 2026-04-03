#  EDA 보고서(3월 과제) — Blood Transfusion Service Center 데이터 분석

>  | 2555031 이지원 | 2026.03.23

---

##  프로젝트 개요

대만 신주시 헌혈 서비스 센터(Blood Transfusion Service Center)의 RFMTC 데이터셋(748건)을 활용하여 **탐색적 데이터 분석(EDA)**을 수행한 과제입니다.

혈액은 인공 제조가 불가능한 부패성 자산으로, JIT(Just-In-Time) 공급망 관점에서 헌혈자 행동 패턴을 분석하고 운영 효율 개선 인사이트를 도출하는 것을 목적으로 합니다.

---

##  파일 구성

| 파일명 | 설명 |
|--------|------|
| `EDA_보고서_혈액헌혈_이지원_2555031.pdf` | EDA 분석 보고서 (최종 제출본) |
| `EDA_혈액헌혈_코랩코드.ipynb` | Google Colab 분석 코드 (Python) |
| `README.md` | 프로젝트 설명 문서 |



---

##  데이터셋 정보

- **출처**: [OpenML (ID: 1464)](https://www.openml.org/d/1464) / UCI Machine Learning Repository
- **원본 논문**: Yeh et al. (2008), *Knowledge discovery on RFM model using Bernoulli sequence*
- **규모**: 748행 × 5열

| 변수명 | RFMTC | 의미 | 단위 |
|--------|-------|------|------|
| Recency | R | 마지막 헌혈 이후 경과 시간 | 월 |
| Frequency | F | 총 헌혈 횟수 | 회 |
| Monetary | M | 총 헌혈량 | c.c. |
| Time | T | 첫 헌혈 이후 경과 시간 | 월 |
| Class | C | 2007년 3월 헌혈 여부 (타겟) | 1=헌혈, 0=미헌혈 |

---

##  분석 목차

### 1. 서론
- 분석 배경 및 목적 (혈액 공급망 JIT 관점)
- 비즈니스 문제 정의 (수요-공급 역전, 폐기 vs 부족, 헌혈자 유지)
- 데이터셋 설명 및 4가지 가설 설정

### 2. 데이터 프로파일링
- 데이터 불러오기 (openml, fetch_openml, StringIO, requests 4가지 방법)
- 데이터 명세 확인 (`df.info()`, `df.shape`)
- 결측치 분석 및 기초 통계량 분석
- 데이터 정제 (중복 행 제거, IQR 기반 이상치 처리)

### 3. 단변량 분석 (Univariate Analysis)
- 수치형 변수별 히스토그램 + KDE, 왜도/첨도 분석
- 범주형 변수(Class) 빈도 분석 및 클래스 불균형 확인
- 파생 변수 생성 (Recency/Frequency Binning)

### 4. 다변량 분석 (Multivariate Analysis)
- 상관계수 히트맵 및 다중공선성 검토
- 산점도 분석
- Class 기반 심층 분석 (Box plot / Violin plot)
- 세그먼트별 비교 (저빈도 vs 고빈도 헌혈자)

### 5. 핵심 인사이트 및 가설 검증
- 주요 패턴 발견 3가지
- 4가지 가설 채택/기각 결과 및 근거
- 예상치 못한 발견 (채찍 효과, 기상 경제학적 리스크, JIT 회복 제약 가설의 한계)

### 6. 결론 및 향후 방향
- 분석 요약 및 비즈니스 제언
- 한계점 및 추후 과제

---

## 🛠 사용 기술

- **분석 환경**: Google Colab (Python 3)
- **주요 라이브러리**: pandas, numpy, matplotlib, seaborn, scipy
- **데이터 수집**: openml, sklearn.datasets, requests

---

##  실행 방법

1. `EDA_혈액헌혈_코랩코드.ipynb` 파일을 Google Colab에서 열기
2. 런타임 → 모두 실행 (`Ctrl + F9`)
3. 데이터는 OpenML에서 자동으로 불러오므로 별도 다운로드 불필요

---

##  참고사항

- 본 보고서는 **데이터관리론** 수업 과제로 작성되었습니다.
- EDA 단계이므로 인과관계가 아닌 **상관관계** 분석에 해당합니다.
- 향후 로지스틱 회귀, 랜덤 포레스트 등 머신러닝 모델을 통한 재헌혈 예측 모델 구축을 추후 과제로 제안합니다.
