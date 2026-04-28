---
tags: [기술적분석, 거래량, OBV, 거래량선행, 다이버전스]
date: 2026-04-28
source_count: 1
---

# OBV (On-Balance Volume)

> 관련 지표: [[이동평균선]] | [[MACD]] | [[RSI]] | [[볼린저밴드]] | [[스토캐스틱]] | [[TA_Index]]

---

## 1. 계산 로직

### 1-1. 기본 산식

$$\text{OBV}_{t} = \text{OBV}_{t-1} + \begin{cases} +\text{거래량}_t & \text{(종가} > \text{전일 종가)} \\ -\text{거래량}_t & \text{(종가} < \text{전일 종가)} \\ 0 & \text{(종가} = \text{전일 종가)} \end{cases}$$

- **개발**: Joseph Granville (1963)
- **핵심 원리**: "거래량이 주가보다 선행한다" (Volume precedes price)
- OBV 자체의 절댓값보다 **방향과 추세**가 중요

### 1-2. OBV-EMA 파생 지표

$$\text{OBV-EMA}(n) = EMA(n) \text{ of OBV}$$

- 기본값: n = 20일
- OBV선과 OBV-EMA의 교차를 매매 신호로 활용

---

## 2. 매수 트리거

| 신호 유형 | 조건 |
|-----------|------|
| **강세 다이버전스** | 주가 저점이 낮아지는데 OBV는 저점이 높아짐 → 매수세 유입 → 주가 반등 예고 |
| **OBV 신고점 돌파** | OBV가 이전 고점을 경신 → 강한 상승 추세 확인 |
| **OBV-EMA 골든크로스** | OBV가 OBV-EMA(20)를 **상향 돌파** → 매수 신호 |
| **OBV 상승 + 주가 횡보** | 주가가 박스권에서 OBV가 계속 오름 → 상방 돌파 임박 |

---

## 3. 매도 트리거

| 신호 유형 | 조건 |
|-----------|------|
| **약세 다이버전스** | 주가 고점이 높아지는데 OBV는 고점이 낮아짐 → 매도세 유입 → 주가 하락 예고 |
| **OBV 신저점 돌파** | OBV가 이전 저점을 경신 → 하락 추세 가속 확인 |
| **OBV-EMA 데드크로스** | OBV가 OBV-EMA(20)를 **하향 돌파** → 매도 신호 |
| **OBV 하락 + 주가 횡보** | 주가가 박스권에서 OBV가 계속 내려감 → 하방 돌파 임박 |

---

## 4. 한계점 및 주의사항

- **비정상 거래량 왜곡**: 배당락일, 공매도 청산, 대규모 ETF 리밸런싱 등 이벤트성 거래량은 OBV를 크게 왜곡 → 오신호 발생
- **절댓값 무의미**: OBV의 숫자 자체는 의미가 없으며, 추세 방향과 다이버전스만 분석
- **단독 사용 한계**: [[이동평균선]] 방향 또는 [[볼린저밴드]] 스퀴즈와 함께 확인하면 신뢰도 향상
- **거래량 데이터 품질 의존**: 장외 거래, ETF 간접 영향 등 불완전한 거래량 데이터 시 왜곡

---

## 5. 실전 활용 전략

### OBV-EMA 크로스 전략

```python
import yfinance as yf
import pandas as pd

ticker = yf.download("005930.KS", period="1y")
ticker['OBV'] = (
    ticker['Volume'] * (
        (ticker['Close'] > ticker['Close'].shift(1)).astype(int) -
        (ticker['Close'] < ticker['Close'].shift(1)).astype(int)
    )
).cumsum()
ticker['OBV_EMA20'] = ticker['OBV'].ewm(span=20).mean()

# 매수: OBV > OBV_EMA20
# 매도: OBV < OBV_EMA20
```

### 거래량 선행성 활용
```
조건 1: OBV가 이전 고점을 먼저 돌파 (주가는 아직 이전 고점 미달)
조건 2: [[볼린저밴드]] 스퀴즈 상태 확인
조건 3: 주가가 전고점 돌파 시 매수 진입 → OBV가 선행 확인된 강한 상승 기대
```
