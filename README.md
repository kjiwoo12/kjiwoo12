## 김지우 · 공인회계사

감사원에서 공공부문 결산검사 및 회계감리를 수행했습니다. 지금은 **감사인의 판단 절차를 LLM 에이전트로 옮기는 일**에 관심이 있습니다.

재무제표를 읽는 일은 숫자를 정리하는 일이 아니라, 숫자들 사이의 어긋남을 찾는 일입니다. 정리는 도구가 이미 잘 합니다. 어긋남을 어디서 어떻게 찾아야 하는지를 아는 것 — 그게 회계사가 AI에 넣을 수 있는 고유한 값이라고 생각합니다.

### 프로젝트

**[공공부문 재정 스크리너](https://github.com/kjiwoo12/public-finance-screener)** — 감사 대상 선정 도구
<br><sub>지방공기업 427곳 · 5개년 1,620건 전수 · 정부 API 6종 · 테스트 54개 · [산출물 검토조서 보기](https://kjiwoo12.github.io/public-finance-screener/workpaper.html)</sub>

지방공기업 427곳의 공개 결산자료를 전수로 훑어 확인이 필요한 기관·연도를 고릅니다. 올린 16건보다 **올리지 않은 1,604건의 사유를 세어서 남기는 것**이 요점입니다 — 감사 대상 선정에서 정작 답해야 하는 질문은 "그럼 저기는 왜 안 봤나"이기 때문입니다. 산출물은 감사조서 서식(모집단·적용 절차·제외·발견사항)으로 나갑니다. 감사원 자료로 채점을 시도했으나 불가능했고, 왜 불가능한지를 저장소에 그대로 적었습니다.

**[Audit Signal Agent](https://github.com/kjiwoo12/audit-signal-agent)** — 회계 이상징후 발굴 에이전트
<br><sub>감사 절차 Skill 6종 · 결정론적 도구 4종 · 테스트 103개 · 정답지 기반 채점기 · AI 없는 대조군 6/7 · [산출물 감사조서 보기](https://kjiwoo12.github.io/audit-signal-agent/report/baseline.html)</sub>

여러 시스템(총계정원장·판매·물류·원가·은행)에 흩어진 데이터를 교차 검증해, 개별 파일만 봐서는 보이지 않는 문제를 찾습니다. 감사 절차를 Skill 파일로 코드화하고, 모든 발견사항에 원본 전표번호를 근거로 붙입니다. 숫자 검증은 Python이, 가설 생성과 설명은 LLM이 담당하도록 경계를 나눴습니다.

**[DART 재무분석기](https://github.com/kjiwoo12/-dart-dash)** — 재무제표 비교 자동화
<br><sub>DART Open API · CLI + 웹 UI · Vercel 배포 · [라이브 데모](https://dart-dash-sdlc.vercel.app/)</sub>

회사명만 입력하면 DART Open API에서 3개 회사의 최근 3개년 연결재무제표를 조회해 핵심 항목과 재무비율을 비교하고 엑셀로 내려줍니다. CLI와 웹 UI를 함께 제공하며 Vercel에 배포했습니다.

### 에이전트를 이렇게 짭니다

말로 하는 관심사 대신, 실제로 코드에서 지킨 규칙을 적습니다.

- **숫자는 코드, 판단은 LLM.** 모델이 합계·비율을 직접 계산하는 경로를 아예 막았습니다. 계산은 결정론적 도구([`tools/`](https://github.com/kjiwoo12/audit-signal-agent/tree/main/tools))만 합니다. 회계에서 숫자 하나가 틀리면 보고서 전체를 못 씁니다.
- **감사 절차 = Skill 파일.** 절차를 프롬프트에 녹이지 않고 [`skills/`](https://github.com/kjiwoo12/audit-signal-agent/tree/main/skills) 아래 6개 마크다운으로 분리했습니다. 절차를 고치는 사람이 코드를 몰라도 됩니다.
- **근거 없는 주장은 코드가 강등합니다.** 원본과 대조되지 않은 인용은 발견사항이 아니라 '미확인 가설'로 내려갑니다([`agent/evidence.py`](https://github.com/kjiwoo12/audit-signal-agent/blob/main/agent/evidence.py)). 지어낸 전표번호로는 정답 처리를 받을 수 없습니다.
- **정답지를 먼저 쓰고 채점기를 만듭니다.** 데이터를 생성할 때 문제 7개와 함정 4개를 심고 목록을 따로 뒀습니다([`scoring/`](https://github.com/kjiwoo12/audit-signal-agent/tree/main/scoring)). 채점기 자신을 모범답안으로 먼저 검증합니다.
- **판정할 수 없는 것은 판정하지 않습니다.** 인과 연결(Level 3·4)은 규칙으로 못 가립니다. 점수를 지어내는 대신 사람이 읽을 지점만 좁혀 줍니다.
- **대조군을 먼저 세웁니다.** AI를 뺀 규칙 기반 버전이 7개 중 6개를 찾았습니다. 예상(4~5개)이 틀렸고 틀린 대로 적었습니다. AI의 값은 탐지율이 아니라 규칙이 못 한 것 — 기각 기록과 인과 서술 — 에 있다는 결론이 여기서 나왔습니다.

### 관심 분야

`LLM Agent 설계` · `Agentic Harness / Skills` · `회계 감사 절차 자동화` · `원가·수익성 분석`

### 연락

[kjiwoo95@gmail.com](mailto:kjiwoo95@gmail.com) · [소개 페이지](https://kjiwoo12.github.io)
