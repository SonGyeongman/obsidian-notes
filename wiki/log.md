# 위키 변경 로그

이 파일은 append-only 연대기입니다. 위키 수정 시마다 아래 형식으로 기록합니다:
`## [YYYY-MM-DD] 작업명 | 요약`

파싱 예시: `grep "^## \[" wiki/log.md | tail -5` → 최근 5개 항목 확인

---

## [2026-04-21] 초기화 | 위키 뼈대 구축 완료

- 폴더 구조 생성: `raw_sources/`, `wiki/`, `wiki/종목/`, `wiki/거시경제/`, `wiki/투자원칙/`
- `wiki/index.md` 초기화 (카테고리별 목차 템플릿)
- `wiki/log.md` 초기화 (이 파일)
- `CLAUDE.md` 스키마 파일 생성 (위키 관리 규칙 정의)

## [2026-04-21] 구조 확장 | 도서·투자전략 카테고리 추가

- 폴더 생성: `wiki/도서/` (전문 서적 요약 및 챕터별 목차 정리)
- 폴더 생성: `wiki/투자전략/` (구체적인 매매 기법, 지표 활용법, 진입·청산 전략)
- `CLAUDE.md` 업데이트: 디렉토리 구조 설명, tags 카테고리 목록, Ingest 워크플로우에 두 카테고리 반영

## [2026-04-21] 스키마 갱신 | 행동 강령(The Execution Harness) 규칙 6 추가

- `CLAUDE.md` 규칙 6 신설: 파일 수정 전 `<plan>` 태그로 (1)대상 파일, (2)모순 여부, (3)YAML 준수 확인 후 `<execute>` 진행

## [2026-04-28] ingest | 피터 린치 관련 소스 5건 → wiki/투자전략/피터린치_6가지분류.md 신규 생성

- 처리 파일: `strategy_peter_lynch_6types.md`, `strategy_peter_lynch_book_summary.md`, `report_peter_lynch_PEG_strategy.md`, `report_peter_lynch_risk_management.md`, `paper_peter_lynch_india_validation.md`
- 생성: `wiki/투자전략/피터린치_6가지분류.md` — 4-섹션 구조(분류 체계 / 실전 기업 사례 / 검증 및 지표 / 리스크 관리) 집대성
- 주요 내용: 6유형 정의·비교표, 엔비디아·삼성전자·POSCO·HMM 등 실전 사례 매칭, PEG 알고리즘화, 인도 BSE 100 12년 실증(2005~2017) 수록, 유형별 매도 신호 체계화
- 수정: `wiki/index.md` — 투자전략 테이블에 피터린치 행 추가, 출처 요약 5건 추가
- 교차 참조 추가: [[CAN_SLIM]], [[마법공식]], [[투자원칙]], [[거시경제]]

## [2026-04-28] ingest | 마법공식 관련 소스 5건 → wiki/투자전략/마법공식.md 신규 생성

- 처리 파일: `strategy_magic_formula.md`, `strategy_magic_formula_v3.md`, `strategy_magic_formula_v4.md`, `paper_magic_블로그.md`, `paper_testing_magic_formula.md`
- 생성: `wiki/투자전략/마법공식.md` — 4-섹션 구조(이론 / 한국 실전 세팅 / 통계 검증 / 운용 가이드) 병합
- 특이사항: `paper_testing_magic_formula.md` 본문에 호주 합병법 논문 오첨부 확인 → 나의 메모 요약만 반영, 파일 내 경고 주석 삽입
- 수정: `wiki/index.md` — 투자전략 테이블에 마법공식 행 추가
- 교차 참조 추가: [[CAN_SLIM]], [[투자원칙]], [[거시경제]]

## [2026-04-28] ingest | CAN SLIM 학술 논문 4건 → wiki/투자전략/CAN_SLIM.md 신규 생성

- 처리 파일: `strategy_CAN_SLIM.md`, `paper_CANSLIM_나스닥_OPBM.md`, `paper_CANSLIM_AAII_백테스트.md`, `paper_CANSLIM_신흥국_한계.md`, `paper_CANSLIM_학술검증_요약.md`
- 생성: `wiki/투자전략/CAN_SLIM.md` — 7가지 체크리스트 + 실전 스크리닝 셋업(AAII 3모델 비교) + OPBM II 간소화 모델(4기준 비교표 + 백테스트 결과) + 학술 검증 결과 및 한계점(긍정·부정 대비, 신흥국 경고, 슬리피지 경고) 통합 구성
- 수정: `wiki/index.md` — 투자전략 카테고리 섹션 신설, CAN_SLIM 행 및 출처 요약 5건 추가

## [2026-04-28] ingest | 거시경제 소스 1건 → wiki/거시경제/매크로_인과관계_매뉴얼.md 신규 생성

- 처리 파일: `macro_causality_manual.md`
- 생성: `wiki/거시경제/매크로_인과관계_매뉴얼.md` — 금리/환율/VIX 3대 지표의 [인과관계 로직→수혜→피해 섹터] 구조화
  - 금리 인상기: 은행·보험·필수소비재 수혜 / 바이오·성장 IT·부동산 피해
  - 금리 인하기: IT·바이오·친환경 수혜 / 은행·보험 피해
  - 고환율: 반도체·자동차·조선 수혜 / 항공·음식료 피해
  - VIX 구간별 기계적 행동 지침 (≤15·15~20·20~30·30~40·≥40)
  - 복합 시나리오 사전 5종 (최악공포·황금기·스태그플레이션·연착륙·원화강세)
- 교차 참조: [[마법공식]], [[CAN_SLIM]], [[피터린치_6가지분류]], [[이동평균선]], [[RSI]], [[볼린저밴드]], [[MACD]], [[TA_Index]]
- 수정: `wiki/index.md` — 거시경제 섹션 헤더를 "거시경제 및 시황"으로 갱신 + 매크로_인과관계_매뉴얼 행 추가

## [2026-04-28] ingest | 기술적분석 지표 소스 9건 → wiki/기술적분석/ 폴더 신규 생성

- 처리 파일: `이동평균선.md`, `RSI.md`, `Stochastic.md`, `볼린저밴드.md`, `OBV.md`, `MACD.md`, `paper_이동평균선_A.md` (Han,Yang,Zhou 2013), `paper_이동평균선_B.md` (Han,Zhou,Zhu 2016), `paper_이동평균선_C.md` (Brogaard,Zareei ML)
- 생성: `wiki/기술적분석/이동평균선.md` — 추세 지표, SMA 산식·5단계 기간별 의미·정배열/역배열·골든/데드크로스 + 논문 A/B 학술 검증 섹션
- 생성: `wiki/기술적분석/MACD.md` — 추세+모멘텀 지표, EMA(12-26)·시그널·히스토그램 + CSI 300 MACD 최적화 논문 검증 (박철호 2023)
- 생성: `wiki/기술적분석/RSI.md` — 모멘텀 지표, RSI(14) 산식·과매수/과매도·다이버전스·Failure Swing·RSI(2) 전략
- 생성: `wiki/기술적분석/스토캐스틱.md` — 모멘텀 지표, %K/%D 산식·골든/데드크로스·Stochastic Pop·Fast vs. Slow 비교
- 생성: `wiki/기술적분석/볼린저밴드.md` — 변동성 지표, 20MA±2σ·%b·밴드폭·스퀴즈→돌파·Walking the Band·W자 바닥
- 생성: `wiki/기술적분석/OBV.md` — 거래량 지표, 누적 거래량 산식·강세/약세 다이버전스·OBV-EMA 크로스·Python 코드
- 생성: `wiki/기술적분석/TA_Index.md` — 기술적 분석 총람, 4카테고리 분류 + 지표 조합 전략 3가지 + 학술 검증 요약
- 수정: `wiki/index.md` — 기술적분석 카테고리 섹션 신설, 7개 페이지 행 추가, date 갱신
- 특이사항: `paper_이동평균선_A.md` (12줄 stub), `paper_이동평균선_B.md`·`C.md` (본문 내용 토큰 초과로 논문 제목·저자·나의 메모만 추출) — 논문 요지는 지식 기반에서 보완하여 학술 검증 섹션 작성
