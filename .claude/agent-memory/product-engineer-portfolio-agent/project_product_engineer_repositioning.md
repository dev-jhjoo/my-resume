---
name: project-product-engineer-repositioning
description: my-resume 저장소를 Product Engineer 포지셔닝으로 전환하는 진행 중인 작업 (2026-07-11 시작)
metadata:
  type: project
---

저장소는 단일 파일(`index.html`, 인라인 CSS/JS, 빌드 도구 없음)로 구성된 정적 웹 이력서. 탭 3개(`#resume` 이력서 / `#cv` 경력기술서 / `#portfolio` 포트폴리오)를 hash 기반 JS로 전환. `@media print` 규칙으로 PDF 저장 지원.

**진행 상황 (2026-07-11)**
- `docs/product-engineer-portfolio-audit.md`, `docs/product-engineer-rebranding-plan.md` 작성 완료.
- 1차 구현 완료: (1) Hero 포지셔닝 개편 — title/meta/OG/Twitter, topbar brand label, h1 sublabel, tagline, lead, footer. (2) Morning Report Alpha를 Problem/Hypothesis/MVP/My Role/Key Decisions/Current Result/Learnings/Next/Technology 구조의 Product Case Study로 전환.
- 기존에 이전 FDE 포지셔닝 때 만들어졌다가 제거된 "대표 문제 해결 사례" 섹션의 CSS(`.case__meta`, `.case-result`)가 죽은 코드로 남아있던 것을 재활용함 (감사 문서에 기록).
- 사실관계 미확인 항목은 전부 `<span class="todo-flag">[TODO: ...]</span>`로 시각적으로 표시(대시 밑줄 스타일, 눈에 띄게) — 코드에 숨겨진 TODO 주석이 아니라 실제 페이지에서 보이게 함으로써 사용자가 놓치지 않도록 함.
- **Hero CTA는 프로토타입 후 제거됨.** 처음에 Products/Experience/Resume/Contact 링크 row를 hero에 추가했었는데(동작시키려면 JS를 `.tab`에서 `[data-view]` 전체로 확장해야 했음), 사용자가 "hero-cta 부분은 없는게 좋을 것 같아"라고 명시적으로 요청해 마크업·CSS(`.hero-cta`,`.cta-link`,`.cta-link--primary`)·JS 확장을 전부 되돌림. **앞으로 hero에 CTA 버튼/링크 row를 다시 추가하지 말 것** — 새로운 명시적 요청이 없는 한.

**사용자가 명시적으로 결정한 사항 (2026-07-11, 더 이상 열린 질문 아님)**
- WishLamp / 헤어 필기시험 퀴즈 / 경로탐색 MCP → **제외**. 사이트에 추가하지 않음.
- AI Product Lab / "100 AI Products" → **아직 초기 단계라 제외**. 다시 만들라는 요청이 없는 한 착수하지 말 것.
- FDE 포지셔닝 → **완전 삭제 완료**. `index.html`에 "FDE" 문자열 0건 확인됨.

**Morning Report Alpha 케이스 스터디 TODO 전부 해결 (2026-07-11)**
사용자가 실제 사실을 알려줘서 `.todo-flag`로 표시했던 5곳을 모두 실제 문장으로 교체함:
- 계기(Problem): 최근 주식 시장 활황 대비 본인의 지식 부족을 느껴, AI로 투자 심리를 분석해보고 싶었던 개인적 동기.
- 가설(Hypothesis): "종목별 뉴스 기사 분석 점수와 실제 시장 가격의 움직임이 비슷할 것이다."
- 실사용 지표(Current Result): 빈도·피드백·정확도는 아직 검증 진행 중(수치 없이 "진행 중"이라는 사실 그대로 기술 — 수치를 지어내지 않음).
- 배운 점(Learnings): AI 자동화에는 분석 실패·타임아웃·API rate limiting 같은 돌발 상황에 대한 세심한 예외 처리가 필요하다는 것을 배움.
- Next: 약 한 달간 데이터 수집·결과 확인 후 실제 투자 진행 여부 판단.
현재 이 케이스 스터디에는 열린 TODO가 없음. `.todo-flag` CSS는 향후 다른 케이스 스터디에 재사용할 수 있도록 스타일시트에 남겨둠(현재는 미사용).

**Experience(경력) 섹션 재구성 완료 (2026-07-11)**
- `#resume` 탭 "경력" job 불릿 7개사(케이피모바일/커넥틴/카닥/에이피엠멤버스/에어프레미아/엔에치엔케이씨피/엑심베이) — 커밋 `acb0a7c`.
- `#cv` 탭(경력기술서) 회사별 story 카드 5개사(케이피모바일/커넥틴/에이피엠멤버스/에어프레미아/엑심베이)의 "담당 업무"·"기여 포인트" 불릿도 동일 원칙으로 재구성 완료 (라벨 구조 담당직무/기술스택/담당 업무/기여 포인트는 유지, 내용만 문제→행동→임팩트로 재배열) — 커밋 `3a7a777`.
- 두 곳 다 날짜·수치·태그·회사명은 전혀 건드리지 않음. 새 사실은 추가하지 않았고, 같은 문서 내 이미 있던 사실(예: 케이피모바일의 기존 SQL 기반 TPS 제어/동기식 Socket 통신)만 문제 맥락으로 앞으로 끌어옴.
- 에이피엠멤버스의 "기여 포인트"(가입자 1.7만 명, 상품권 판매 60억 원 등 수치)는 이미 임팩트 중심이라 내용 변경 없이 그대로 둠 — 순서/라벨도 안 건드림.

**기술과 실행 범위(skill panels) 재구성 완료 (2026-07-11, 아직 미커밋)**
`#resume` 탭 4개 스킬 패널을 기술 카테고리 그룹핑(Backend & Integration / Data & Automation / Operations & Resilience / Infra & Delivery)에서 역량 그룹핑(Product Building / Data & AI-assisted Development / Operational Resilience / Cloud & Delivery)으로 재구성. 각 패널의 태그(기술 목록)는 완전히 동일 — 새 기술 추가/삭제 없음, 헤더와 설명 문장만 "이 기술로 무엇을 하는지"에서 "이 역량으로 제품에 어떤 결과를 만드는지"로 재작성. 매핑은 `docs/product-engineer-rebranding-plan.md` §9 참고.

**아직 손대지 않은 영역**
- 일하는 방식(pillars) — 전부 미변경.
- Featured Products 그리드, How I Build, Writing/Build Log — 신규 섹션 전부 미착수.

**Why**: 사용자가 이번 요청에서 범위를 Hero + Case Study 1개로 명시적으로 제한했고, 사실 아닌 성과/지표를 절대 만들지 말라고 강조함. [[feedback-analysis-before-edit-and-visible-todos]] 참고. Hero CTA 제거는 순수 UX 취향 결정(사실관계와 무관).

**How to apply**: Morning Report Alpha 케이스 스터디는 현재 사실관계 기준으로 완결된 상태. 다음 라운드에서 Featured Products/Experience/How I Build 등 새 영역을 진행하려면, 먼저 그 영역에 필요한 사실(다른 프로젝트 존재 여부, 경력 세부 재구성 방향 등)을 사용자에게 확인할 것. WishLamp/AI Product Lab/FDE는 재차 묻지 말고 위 결정을 그대로 따를 것(사용자가 먼저 번복하지 않는 한).
