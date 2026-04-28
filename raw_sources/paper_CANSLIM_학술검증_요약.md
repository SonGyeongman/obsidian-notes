# [논문리뷰] CAN SLIM 전략의 학술적 백테스트 결과 및 한계점
- 분류: 투자전략 / 한계점 검증
- 나의 메모: 이 내용을 기존에 만들어둔 `wiki/투자전략/CAN_SLIM.md` 문서 하단에 `## ⚠️ 학술적 백테스트 결과 및 한계점` 이라는 새로운 목차를 파서 추가해 줘. AI가 종목을 추천할 때 이 전략이 만능이 아님을 반드시 인지하고 리스크를 경고할 수 있도록 만들어야 해.

---

## 📊 1. 강세장에서의 압도적 초과 수익 (긍정적 검증)
미국 학계와 퀀트 투자 기관들의 백테스트 결과, CAN SLIM 전략은 **'상승장(Bull Market)'에서 시장 지수(S&P 500, NASDAQ)를 압도적으로 상회하는 수익률**을 기록하는 것으로 증명되었다.

* **AAII (미국개인투자자협회) 연구 결과:** 1998년부터 2005년까지 AAII의 CAN SLIM 스크리너를 통해 추출된 포트폴리오의 **연평균 수익률(CAGR)은 30.86%**에 달했다. 동 기간 S&P 600 지수의 수익률(9%)을 3배 이상 상회했다. (Schadler and Cotton, 2008)
* **OPBM (Outperform the Broad Market) 연구:** 복잡한 CAN SLIM 7가지를 4가지 필수 지표(실적, 연간성장률 등)로 간소화하여 나스닥 100 지수에 백테스트한 결과, 시장 수익률을 유의미하게 초과 달성했으며 상승장에서 자본을 효율적으로 집중시키는 효과가 입증되었다. (Lutey et al., 2015)

## 📉 2. 학술 연구에서 밝혀진 전략의 치명적 한계점 (주의사항)

### A. 하락장에서의 취약성과 MDD(최대 낙폭) 리스크
CAN SLIM은 기본적으로 '고평가(신고가)된 주식을 더 비싸게 사는' 모멘텀 전략이 섞여 있다. 논문들은 공통적으로 **"M(시장의 방향)이 하락장으로 꺾일 때, 고성장주들이 가장 먼저, 가장 깊게 폭락한다"**고 지적한다. 
따라서 시장이 꺾일 때는 반드시 투자금의 대부분을 현금화해야만 전략이 성립한다.

### B. 신흥국 시장(Emerging Market) 적용의 한계
CAN SLIM은 미국 시장의 방대한 유동성과 투명한 실적 발표를 기반으로 만들어졌다. 
* **인도네시아 시장 백테스트 연구:** 인도네시아 등 신흥국 주식시장에서 CAN SLIM 포트폴리오를 백테스트한 결과, **시장 수익률(Market Return)보다 통계적으로 유의미하게 높은 초과 수익을 내지 못했다**는 논문이 존재한다. 이는 금융 구조가 다른 시장이나 실적 신뢰도가 낮은 증시(한국의 테마주 등)에서는 'C'와 'A' 조건이 무력화될 수 있음을 시사한다.

### C. 잦은 매매로 인한 거래 비용(슬리피지) 문제
"7~8% 하락 시 무조건 기계적 매도"라는 원칙 때문에 변동성이 큰 장세에서는 **'휩쏘(Whipsaw, 샀다 팔았다를 반복하며 손실만 누적되는 현상)'**가 자주 발생한다. 백테스트 상의 수익률이 실제 계좌 수익률로 이어지지 않는 가장 큰 원인으로 '수수료 및 슬리피지'가 지적된다.

---

### 📎 참조 논문 및 연구 자료 (Reference)
1. *OPBM II: An Interpretation of the CAN SLIM Investment Strategy* (Lutey et al., 2015) - 나스닥 100 지수 대상 CAN SLIM 백테스트 연구. [논문 링크](http://www.na-businesspress.com/JAF/LuteyM_LWeb14_5_.pdf)
2. *A CAN SLIM Screen With No Float but Plenty of Lift* (AAII Journal) - 미국개인투자자협회의 장기 백테스트 결과. [기사 링크](https://www.aaii.com/journal/article/a-can-slim-screen-with-no-float-but-plenty-of-lift)
3. *Analysis Performance Portfolio CAN SLIM Evidence in Indonesia Capital Market* (2016) - 신흥국(인도네시아) 시장 적용의 한계점을 다룬 연구. [논문 링크](https://www.researchgate.net/publication/291970230_Analysis_Performance_Portfolio_CAN_SLIM_Evidence_in_Indonesia_Capital_Market)