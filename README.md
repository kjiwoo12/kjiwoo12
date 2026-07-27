## 김지우 · 공인회계사

감사원에서 공공부문 결산검사 및 회계감리를 수행했습니다. 지금은 **감사인의 판단 절차를 LLM 에이전트로 옮기는 일**에 관심이 있습니다.

재무제표를 읽는 일은 숫자를 정리하는 일이 아니라, 숫자들 사이의 어긋남을 찾는 일입니다. 정리는 도구가 이미 잘 합니다. 어긋남을 어디서 어떻게 찾아야 하는지를 아는 것 — 그게 회계사가 AI에 넣을 수 있는 고유한 값이라고 생각합니다.

### 프로젝트

**[공공부문 재정 스크리너](https://github.com/kjiwoo12/public-finance-screener)** — 감사 대상 선정 도구 ([산출물 검토조서 보기](https://kjiwoo12.github.io/public-finance-screener/workpaper.html))

지방공기업 427곳의 공개 결산자료를 전수로 훑어 확인이 필요한 기관·연도를 고릅니다. 올린 16건보다 **올리지 않은 1,604건의 사유를 세어서 남기는 것**이 요점입니다 — 감사 대상 선정에서 정작 답해야 하는 질문은 "그럼 저기는 왜 안 봤나"이기 때문입니다. 산출물은 감사조서 서식(모집단·적용 절차·제외·발견사항)으로 나갑니다. 감사원 자료로 채점을 시도했으나 불가능했고, 왜 불가능한지를 저장소에 그대로 적었습니다.

**[Audit Signal Agent](https://github.com/kjiwoo12/audit-signal-agent)** — 회계 이상징후 발굴 에이전트 ([산출물 감사조서 보기](https://kjiwoo12.github.io/audit-signal-agent/report/baseline.html))

여러 시스템(총계정원장·판매·물류·원가·은행)에 흩어진 데이터를 교차 검증해, 개별 파일만 봐서는 보이지 않는 문제를 찾습니다. 감사 절차를 Skill 파일로 코드화하고, 모든 발견사항에 원본 전표번호를 근거로 붙입니다. 숫자 검증은 Python이, 가설 생성과 설명은 LLM이 담당하도록 경계를 나눴습니다.

**[DART 재무분석기](https://github.com/kjiwoo12/-dart-dash)** — 재무제표 비교 자동화 ([라이브 데모](https://dart-dash-sdlc.vercel.app/))

회사명만 입력하면 DART Open API에서 3개 회사의 최근 3개년 연결재무제표를 조회해 핵심 항목과 재무비율을 비교하고 엑셀로 내려줍니다. CLI와 웹 UI를 함께 제공하며 Vercel에 배포했습니다.

### 관심 분야

`LLM Agent 설계` · `Agentic Harness / Skills` · `회계 감사 절차 자동화` · `원가·수익성 분석`

### 연락

[kjiwoo95@naver.com](mailto:kjiwoo95@naver.com) · [소개 페이지](https://kjiwoo12.github.io)
