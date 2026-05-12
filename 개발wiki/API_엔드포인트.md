# 확인된 토스증권 API 엔드포인트

> 출처: rpc-catalog.md (tossinvest-cli), 실제 Network 탭 캡처, 역공학
> 모든 인증 필요 엔드포인트는 `Domain=.tossinvest.com` 세션 쿠키 필요

---

## 호스트 역할 분류

| 호스트 | 역할 |
|--------|------|
| `wts-api.tossinvest.com` | 코어 런타임·세션·로그인 |
| `wts-info-api.tossinvest.com` | 시장 데이터·시세·랭킹 (공개) |
| `wts-cert-api.tossinvest.com` | 인증 필요 개인 데이터·자산 |
| `sse-message.tossinvest.com` | SSE 알림 채널 |

---

## 현재 확장 프로그램이 사용하는 엔드포인트

### inject.js — 인터셉트 대상 (토스 웹앱이 자동 호출)

| 이벤트 타입 | 메서드 | 호스트 | 경로 | 응답 주요 필드 |
|------------|--------|--------|------|--------------|
| `TOSS_RANK_DATA` | GET | `wts-info-api` | `/api/v1/rankings/realtime/stock` | `result.data[].symbol/name/market.code` |
| `TOSS_RANKING_DATA_US` | POST | `wts-cert-api` | `/api/v2/dashboard/wts/overview/ranking` | `result.products[].rank/productCode/name/price.close/extraInfo` |
| `TOSS_CHART_HISTORY` | GET | `wts-info-api` | `/api/v1/c-chart/us-s/{ticker}/min:1` | `result.code/candles[].dt/close/nextDateTime` |
| `TOSS_QUOTES_DATA` | GET | `wts-info-api` | `/api/v2/stock/quote*` | `productCode/currentPrice` |
| `TOSS_COMMUNITY_DATA` | GET | - | `/api/v1/community/posts` | (TODO: 구조 미확인) |

### inject.js — 폴링 (inject.js가 직접 호출, 60초 주기)

| 이벤트 타입 | 메서드 | 호스트 | 경로 | 응답 주요 필드 |
|------------|--------|--------|------|--------------|
| `TOSS_ASSET_SUMMARY` | GET | `wts-cert-api` | `/api/v3/my-assets/summaries/markets/all/overview` | `result.total_asset_amount/profit_rate` |
| `TOSS_ASSET_SUMMARY` | GET | `wts-cert-api` | `/api/v1/dashboard/common/cached-orderable-amount` | `result.orderableAmountUs.usd` |
| `TOSS_PORTFOLIO` | POST | `wts-cert-api` | `/api/v2/dashboard/asset/sections/all` | `result.sections[{type:"SORTED_OVERVIEW", data.products[].items[]}]` |

### background.js — 직접 호출

| 목적 | 메서드 | 호스트 | 경로 | 비고 |
|------|--------|--------|------|------|
| 가격 폴링 | GET | `wts-info-api` | `/api/v1/product/stock-prices?meta=true&productCodes=...` | 30초 주기 |
| 차트 히스토리 시드 | GET | `wts-info-api` | `/api/v1/c-chart/us-s/{ticker}/min:1?count=397` | 신규 종목 최초 1회 |
| SSE 알림 채널 | GET | `sse-message` | `/api/v1/wts-notification` | 상시 연결 |
| Ollama AI 판단 | POST | `localhost:11434` | `/api/generate` | 신호 발생 시 |
| RAG 위키 검색 | POST | `localhost:8000` | `/api/rag/search` | 신호 발생 시 |
| Discord 알림 | POST | `discord.com` | `/api/webhooks/...` | BUY 신호 시 |
| Obsidian 저장 | PUT | `127.0.0.1:27124` | `/vault/Trading_Logs/{filename}.md` | BUY 신호 시 |

---

## 포트폴리오 API 응답 구조 상세

### `/api/v2/dashboard/asset/sections/all` 응답

```json
{
  "result": {
    "sections": [
      {
        "type": "SORTED_OVERVIEW",
        "data": {
          "products": [
            {
              "marketType": "US",
              "items": [
                {
                  "stockSymbol": "AAPL",
                  "stockCode": "US...",
                  "stockName": "애플",
                  "quantity": 10,
                  "currentPrice": { "usd": 185.5, "krw": 250000 },
                  "purchasePrice": { "usd": 170.0, "krw": 230000 },
                  "profitLossRate": { "usd": 0.091, "krw": 0.087 },
                  "dailyProfitLossAmount": { "usd": 12.5, "krw": 16800 }
                }
              ]
            }
          ]
        }
      }
    ]
  }
}
```

> **주의**: `profitLossRate`는 소수(0.091 = 9.1%). inject.js에서 ×100 처리.

---

## 차트 API 응답 구조

```json
{
  "result": {
    "code": "NAS0240905004",
    "candles": [
      { "dt": "2026-05-08T13:51:00-04:00", "close": 185.5 }
    ],
    "nextDateTime": "2026-05-07T09:30:00-04:00"
  }
}
```

---

## 인증 헤더 요구사항

```
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 ...
Referer: https://www.tossinvest.com/
credentials: 'include'   (쿠키 자동 포함)
```

> Go 기본 User-Agent(`Go-http-client/1.1`)는 403 차단됨 (역공학 확인).
