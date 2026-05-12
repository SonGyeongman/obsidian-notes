# 토스증권 AI 자동매매 확장 프로그램 — 개발 위키

> **프로젝트 경로**: `D:\주식확장프로그램`
> **최초 개발 시작**: 2026-04-28
> **최근 업데이트**: 2026-05-10

---

## 프로젝트 개요

토스증권(www.tossinvest.com) 웹 브라우저에서 동작하는 **Chrome MV3 확장 프로그램**.
토스증권 API를 실시간으로 가로채어 주가·지표를 계산하고, Qwen2.5:14b LLM이 매수/관망/매도를 판단해 Discord + Obsidian으로 알림을 보낸다.

### 핵심 기능

| 기능 | 상태 |
|------|------|
| 실시간 주가 수신 (SSE + REST 폴링) | ✅ 완료 |
| 기술적 지표 계산 (MA5/20/60/120, MACD, BB, RSI) | ✅ 완료 |
| 골든크로스 / RSI 과매도 신호 감지 | ✅ 완료 |
| Qwen2.5:14b AI 매매 판단 | ✅ 완료 |
| 투자 원칙 위키 RAG 검색 | ✅ 완료 |
| Discord Webhook 알림 | ✅ 완료 |
| Obsidian 매매일지 자동 저장 | ✅ 완료 |
| 인기 순위 100 가로채기 | ✅ 완료 |
| 해외주식 거래대금 랭킹 (수급) | ✅ 완료 |
| 개인 자산 요약 조회 | ✅ 완료 |
| 포트폴리오 보유 종목 조회 | ✅ 완료 |
| RAG 서버 (BM25) | ✅ 완료 |

---

## 폴더 구조

```
D:\주식확장프로그램\
├── src\
│   ├── background.js        # Service Worker — 핵심 로직 (지표계산, AI판단, 알림)
│   ├── inject.js            # 페이지 컨텍스트 — fetch/XHR 인터셉터
│   ├── content.js           # isolated world — inject.js 주입 + 메시지 릴레이
│   ├── content.jsx          # React 빌드 엔트리 (content.js를 IIFE로 컴파일)
│   └── panel\
│       ├── panel.html       # 확장 팝업 HTML
│       ├── index.jsx        # 팝업 React 엔트리
│       └── components\
│           ├── RankScanner.jsx    # 인기순위 + 수급 UI
│           └── SettingsModal.jsx  # 설정 화면 (Ollama URL, Discord, Obsidian 키)
├── dist\                    # 빌드 결과물 (Chrome에 로드하는 폴더)
│   ├── background.js
│   ├── inject.js
│   ├── content.js
│   ├── manifest.json
│   └── panel\
├── build.js                 # 빌드 스크립트 (Vite JS API)
├── vite.config.js           # IDE 지원 / content-only 빌드용
├── manifest.dist.json       # Chrome 확장 매니페스트 (MV3)
├── rag_server.py            # BM25 RAG 서버 (FastAPI, port 8000)
└── package.json
```

```
D:\주식정보\주식투자\
├── wiki\                    # 투자 원칙 위키 (RAG 서버가 인덱싱)
│   ├── 투자원칙\
│   ├── 투자전략\
│   ├── 거시경제\
│   ├── 기술적분석\
│   └── 도서\
├── raw_sources\             # 원본 자료 (읽기 전용)
├── Trading_Logs\            # Obsidian 매매일지 저장 위치
└── 개발wiki\               # 이 폴더 — 개발 문서
    ├── index.md             # 이 파일
    ├── 아키텍처.md
    ├── API_엔드포인트.md
    ├── 데이터_변수_참조.md
    ├── 함수_참조.md
    └── 개발일지\
```

---

## 외부 연동 서비스

| 서비스 | 역할 | 설정 위치 |
|--------|------|-----------|
| Ollama (로컬) | Qwen2.5:14b LLM 실행 | 설정 팝업 → Ollama URL |
| Discord Webhook | BUY 신호 알림 | 설정 팝업 → Webhook URL |
| Obsidian Local REST API | 매매일지 마크다운 저장 (port 27124) | 설정 팝업 → API Key |
| RAG 서버 (로컬) | 투자 원칙 위키 BM25 검색 (port 8000) | `rag_server.py` 직접 실행 |

---

## 위키 페이지 목록

- [[아키텍처]] — 3-레이어 메시지 흐름 (inject → content → background)
- [[API_엔드포인트]] — 확인된 토스증권 REST 엔드포인트 목록
- [[데이터_변수_참조]] — 이벤트 타입, StockState 필드, 페이로드 구조
- [[함수_참조]] — 모든 함수 설명 (inject.js / background.js / rag_server.py)
- [[개발일지/index]] — 개발 이력 목록
