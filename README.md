# 🎬 The Exogenous Impact of OTT Release on Movie Review Ratings, Sentiment, and Emotional Responses

🎓 **Master's Thesis Project (2026)** | **Author**: 손범수 (Son Beom-su)

## 📖 Overview
이 레포지토리는 영화의 OTT(Over-The-Top) 플랫폼 공개가 소비자의 영화 리뷰 평점, 텍스트 감성(Sentiment), 그리고 세부적인 감정적 반응(Emotional Responses)에 미치는 외생적 충격(Exogenous Shock)을 분석한 연구의 코드와 데이터를 담고 있습니다. 

본 연구는 단순히 영화관에서 OTT로 시청 매체가 변화했다는 현상적 서술을 넘어, 물리적 환경의 제약이 없고 지불 비용이 낮은 OTT라는 새로운 플랫폼 전환이 소비자의 내면적 심리(기대-불일치 이론)에 어떠한 영향을 미치는지 규명합니다. 이를 통해 플랫폼 전환이라는 비즈니스 이벤트가 소비자 반응에 미치는 실질적인 인과적 효과를 측정하는 데 목적이 있습니다.

## 🔍 Methodology
본 연구는 경제학, 심리학, 데이터 과학을 융합하여 고급 계량경제 방법론과 자연어처리(NLP) 기법을 활용한 실증 분석을 수행했습니다.

* **Staggered Difference-in-Differences (다중 시점 이중차분법)**: Callaway & Sant'Anna (2021)의 방법론을 채택했습니다. 영화마다 OTT에 처음 공개되는 시점(Treatment Timing)이 다르다는 점을 고려하여, 기존 양방향 고정효과(TWFE)의 편향 한계를 극복하고 플랫폼 전환의 동태적이고 이질적인 인과 효과를 엄밀하게 추정했습니다.
* **Sentiment & Emotion Analysis (감성 및 다차원 감정 분석)**: 
  * `KOBERT`: NSMC 데이터셋으로 학습된 모델을 활용하여 리뷰 텍스트의 긍/부정 이진 감성 극성(Polarity) 점수를 산출했습니다.
  * `KcELECTRA`: KOTE 멀티라벨 감정 데이터셋으로 44개 감정을 학습한 뒤, 이를 Plutchik의 8가지 기본 감정(기쁨, 신뢰, 공포, 놀람, 슬픔, 혐오, 분노, 기대)으로 다시 매핑하여 다차원적인 감정 구조 변화를 측정했습니다.

## 📊 Data
* **분석 대상**: 2020년 1월 1일부터 2025년 4월 30일까지 개봉한 한국 영화 중 관람객 수 1,000명 이상인 영화 165편 (총 11,880건의 패널-월 단위 데이터)
* **데이터 출처**: KOBIS 박스오피스, uNoGS(넷플릭스 출시일), 네이버 영화 관람평(리뷰 크롤링)
* **주요 변수**: 
  * `Outcome Variables`: 월별 리뷰 평점 중앙값(`rating_median`), 폴라리티 중앙값(`polarity_median`), 8대 감정별 최대 확률 점수
  * `Treatment Variable`: 개별 영화의 최초 넷플릭스 공개 일자 기준 처리 지표
  * `Moderating Variable`: 극장 개봉부터 OTT 전환까지 걸린 기간(Release Time)

## 💡 Key Findings
* **전반적 평가의 상승**: OTT 플랫폼 편입 이후 월별 유저 평점과 텍스트의 긍정 감성(Polarity)이 극장 상영기 대비 통계적으로 유의하게 상승했습니다. 이는 기대-불일치 이론 관점에서 OTT 후기 관람자에게서 긍정적 기대불일치(positive disconfirmation, "생각보다 좋았다")가 발생했음을 시사합니다.
* **평가적 감정 중심의 재편**: OTT 전환 이후 기쁨(Joy), 놀람(Surprise), 신뢰(Trust), 기대(Anticipation)와 같은 긍정 및 평가적 감정 표현은 유의하게 증가한 반면, 슬픔, 분노, 혐오 등 영화 서사의 본질적 정서는 일관된 변화가 없었습니다. 
* **개봉-OTT 간격(Release Time)의 이질적 효과**: 극장 개봉 후 OTT 공개까지의 간격이 짧은 최하위 50%(약 3~7개월) 그룹에서만 OTT 전환 이후 긍정적 감성 상승이 강하게 유지되었습니다. 반면 간격이 1년 이상 긴 그룹에서는 유의한 효과가 나타나지 않아, 최근성 편향(Recency Bias)에 따른 윈도우 전략의 중요성을 입증했습니다.

## 🛠 Tech Stack
* **Language**: Python (Data Crawling, NLP), Stata or R (Causal Inference)
* **Data Manipulation & Crawling**: `pandas`, `BeautifulSoup` / `Selenium`
* **NLP & Machine Learning**: `huggingface/transformers`, `KcELECTRA`, `KOBERT`
* **Causal Inference**: `csdid` (Callaway & Sant'Anna Staggered DID 패키지)
* **Visualization**: `matplotlib`, `seaborn`

---
*본 레포지토리는 2026년 2월 일반대학원 비즈니스인포매틱스학과 석사 학위 논문의 연구 내용을 바탕으로 구성되었습니다.*
