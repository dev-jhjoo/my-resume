---
name: project-ax-engineer-repositioning
description: my-resume 저장소를 "Ax Engineer"(사내 AI Transformation Engineer) 포지션에 맞춰 리포지셔닝하는 진행 중인 작업
metadata:
  type: project
---

**용어 정의 (사용자 본인 정의, 2026-07-20 확인)**: "Ax Engineer" = "기업 내 AI를 활용해 반복업무 혹은 병목점을 해결하는 AI Transformation Engineer". 일반적인 AI/LLM 제품 엔지니어나 AI 에이전트 전문 엔지니어와는 결이 다르며, 사내 업무 자동화·프로세스 혁신에 방점이 있다. 커스텀 조어이므로 채용 담당자가 생소하게 느낄 수 있음에 유의.

**[[project-fde-repositioning]]와의 관계**: 이전 FDE(Forward Deployed Engineer) 리포지셔닝 작업의 연장선이지만, 사용자가 방향을 "Ax Engineer"로 더 구체화한 상태. FDE는 client-facing 뉘앙스가 강했던 반면, Ax Engineer는 사내(내부 조직) 대상 AI 자동화에 초점 — 사용자의 실제 경험(사내 운영팀 대상 문제 해결)과 더 잘 맞는 방향.

**2026-07-20 진단 결과 (index.html, 커밋되지 않은 diff 기준)**:
- 지금까지 진행된 변경은 타이틀/메타/브랜드 라벨/footer의 "Backend Engineer" → "Ax Engineer" 기계적 문자열 치환뿐. hero의 h1 span, tagline, lead 문단은 이전 FDE 리포지셔닝 때 만들어진 "AI로 문제를 제품으로 만듭니다" 톤 그대로 유지 — 이는 "AI 제품 빌더" 느낌이라 사용자가 정의한 "사내 반복업무/병목 해결"과는 미묘하게 결이 다름.
- 경력(경력 탭 + 경력기술서 탭) bullet은 전 직장에 걸쳐 AI/자동화 언급이 전무. Kafka 전환, Netty 도입, AWS 3-tier, OAuth, MSA 설계, PSS-VAN 결제 게이트웨이, WeChat Pay 연동 등 순수 백엔드 인프라/결제 성과만 나열됨. 예전 FDE 메모리에 있던 "Emergency Backoffice 장애 대응" 사례도 현재 경력 bullet에는 보이지 않음(케이피모바일 항목에서 빠짐).
- "기술과 실행 범위" 스킬 섹션(Gemini API, LLM Structured Output 등 AI 관련 태그 포함)은 HTML 주석 처리되어 있어 실제 페이지에는 전혀 렌더링되지 않음.
- AI 활용 증거는 사실상 포트폴리오 탭의 개인 프로젝트(Morning Report Alpha, Gemini API 뉴스/시세 분석·자동화 파이프라인)뿐이며, 이마저 "개인" 프로젝트로 명시되어 있어 "사내 업무 자동화" 근거로 바로 쓰기엔 약함.
- 결론: 타이틀만 바꾸고 본문(경력)이 그대로면 채용 담당자에게 "라벨만 바꾼 백엔드 이력서"로 읽힐 위험이 큼.

**확인된 AI 활용 사실 (2026-07-20 사용자 제공, 상세)**: 사용자가 업무에 AI를 활용하기 시작한 것은 현재 재직 중인 (주)케이피모바일이 처음. C++ 레거시(단일 파일에 전 기능이 뒤섞이고 주석·실제 동작 불일치, 네이밍컨벤션도 엉망인 스파게티 코드)를 Java/Spring Boot로 포팅하는 작업에서 AI를 전적으로 활용.
- 사용 도구: Claude Code, ChatGPT Codex 두 개를 함께 사용
- 방식: 두 AI로 각각 독립적으로 전체 코드 분석을 시켜 서로 같은 결과/다른 결과를 비교 파악 → 그 내용을 근거로 본인이 직접 코드 검증 → 레거시 기능을 모두 리스팅 → 기능 단위로 패키징해 포팅 진행 (AI 결과를 그대로 쓰지 않고 사람이 검증하는 단계를 반드시 거침)
- 성과: AI 없이 진행했다면 6개월 이상 예상되던 작업을 약 2개월로 단축
- 참고: 대상 파일명(KShotAssisterDlg.cpp)은 이력서에는 노출하지 않기로 함(사용자 요청)
- **다른 AI 활용 사례가 더 있음** — 사용자가 "다른 ai 활용 작업이 있긴 한데 우선 이 내용부터 정리하고 그 다음 시작하자"고 언급. 이 건 정리 후 다음 대화에서 이어서 청취·반영 필요.

**반영 상태 (2026-07-20)**: 케이피모바일 관련 AI 활용 사례가 index.html 3곳에 모두 반영 완료.
1. 경력기술서 탭 "기여 포인트" 첫 항목(약 1285줄) — 상세 서사 문장
2. 이력서 탭 경력 bullet(약 945줄) — "C++ 레거시 코드(스파게티 구조) Java/Spring Boot 포팅"을 상위 li로, 하위 ul에 "Claude Code·ChatGPT Codex 교차 분석 후 사람 검증" / "6개월→2개월 단축" 2개 sub-bullet
3. 이력서 탭 케이피모바일 tags(약 960줄) — "Claude Code · ChatGPT Codex" 태그 추가
파일명(KShotAssisterDlg.cpp)은 사용자 요청대로 어디에도 노출하지 않음.

**두 번째 AI 활용 사례 — Emergency Backoffice 장애 대응 (2026-07-20 사용자가 회고 문서 전문 공유)**: 케이피모바일에서 2026-07-03 발생한 실제 장애. 물량(메시지) 유통 서버(34번) 물리 디스크 장애로 재기동 불가 → OS 재설치·DB/애플리케이션 복구에 총 8시간 이상 소요(08:15 알림 인지 ~ 16:00 핵심 서비스 정상화). 이 복구 작업과 별개로, 10시경부터 운영팀이 레거시 모놀리식 Java/JSP Backoffice에 접속하지 못해 고객 응대 VOC가 급증하자, 11:30경 AI를 활용해 `emergency-backoffice`(Next.js + mysql2, 고객 정보·실시간 물량 조회 전용 미니 도구)를 긴급 빌드·배포해 본 서버 복구와 병행 운영. 구조적 원인 진단: 기존 Backoffice는 여러 DB 커넥션에 대한 예외 처리가 없어 DB 1개 연결 실패가 전체 서비스 장애로 전파되는 구조였음(장애 격리 부재) — 이 문제 진단 자체도 Ax Engineer 서사에 유효한 소재.
- GitHub 저장소(https://github.com/dev-jhjoo/emergency-backoffice, public) 확인: Next.js 14 + React 18 + mysql2, pages(index/members/monitor/monitor-detail) + lib/db.js, 커밋 1개("init", 2026-07-06) — 즉 장애 당일 급조해 실제 배포하고, 이후(07-06) 정리해 커밋한 것으로 보임. AI SDK 의존성은 없어 앱 자체에 AI 기능이 내장된 게 아니라 "AI로 빠르게 개발"한 사례.
- Notion 회고 원문(https://dev-jhjoo.notion.site/7-3-397c0b2b28b58001b326e6734af685aa)은 JS 렌더링이라 WebFetch로는 못 읽었고, 사용자가 대화에 전문을 붙여넣어 확보함.
- 미확인 정보: 이때 구체적으로 어떤 AI 도구(Claude Code/Codex 등)를 썼는지는 회고문에 명시 안 됨 ("급하게 ai를 활용해"라고만 표현) — bullet 작성 전 확인 필요할 수 있음.
- 이 사례는 지금까지 나온 AI 활용 사례 중 가장 강력함(실제 장애·고객 VOC라는 명확한 비즈니스 임팩트 + "병목을 AI로 해결"이라는 Ax Engineer 정의에 정확히 부합). C++ 포팅 사례가 "효율화"라면 이 사례는 "장애 대응/병목 해소"로 성격이 다르며 두 사례가 상호 보완적.

**반영 상태 (2026-07-20)**: Emergency Backoffice 사례 index.html 2곳에 반영 완료 (AI 도구명은 확인 안 된 채로 "AI"라는 일반 표현으로 처리 — 사용자가 확인 없이 "A, B 둘다 적용해줘"로 진행 승인).
1. 이력서 탭 경력 bullet(케이피모바일, C++ 포팅 항목 바로 다음) — "운영 서버 물리 장애로 레거시 Backoffice 접속이 막힌 상황에서, AI로 Emergency Backoffice 긴급 빌드·배포" + 하위 2개 sub-bullet(서버 복구 병행/DB 커넥션 예외처리 부재 진단)
2. 경력기술서 탭 "기여 포인트"(C++ 포팅 항목 바로 다음) — 상세 서사 문장(상황→AI 활용→성과→구조적 원인 진단)
서버 번호(34/36/38번), VOC 구체 수치, 정확한 장애 타임라인(08:15~16:00) 등 회고문의 세부 사항은 이력서에 넣지 않고 일반화해서 반영함(자체 판단 — 사용자가 명시적으로 요청한 건 아님).

**포트폴리오 편입 여부 논의 (2026-07-20)**: 사용자가 Emergency Backoffice를 포트폴리오 탭에 케이스 스터디로 옮기는 것을 고려 중이며, 동시에 "Ax Engineer라도 결국 product를 만들어 운영하는 게 목적"이라는 이유로 기존 Morning Report Alpha 포트폴리오의 위상도 재고 중. 상담사로서 제시한 의견(사용자에게 아직 최종 확인은 안 받음):
- Emergency Backoffice를 포트폴리오 탭("직접 기획·개발·운영하는 사이드 프로젝트" 문구로 프레이밍된 섹션)에 그대로 옮기는 것은 권하지 않음 — (1) 개인 프로젝트가 아니라 재직 중인 회사의 실제 장애 대응 업무이므로 "사이드 프로젝트" 프레이밍과 맞지 않음, (2) 회고문 수준의 디테일(서버 번호, VOC 급증, DB 버전, 정확한 장애 타임라인, 레거시 시스템 구조적 결함)을 공개 포트폴리오에 그대로 노출하면 현재 재직 중인 회사 이름이 이미 페이지에 명시돼 있는 상태에서 특정 회사의 장애·레거시 문제를 공개적으로 상세히 기술하는 셈이 되어 고용주 관계상 리스크가 있음.
- 대안: 더 풍부한 서사가 필요하면 포트폴리오가 아니라 이력서/경력기술서 쪽에 [[project-fde-repositioning]] 때 있었던 case-grid 스타일의 "대표 문제 해결 사례" 하이라이트를 되살리되, 세부사항은 지금 반영한 bullet 수준으로 일반화 유지를 추천.
- Morning Report Alpha는 계속 포트폴리오에 유지 권장 — 경력/경력기술서의 AI 사례가 "사내 병목을 AI로 해결"(Ax Engineer 정의 직접 증거)을 보여준다면, Morning Report Alpha는 "기획부터 운영까지 0→1 제품을 혼자 만들고 운영한 경험"(제품 오너십)을 보여줌. 사용자가 언급한 "결국 product를 만들어 운영하는 게 목적"이라는 동기와 정확히 맞닿아 있어 두 트랙이 경쟁이 아니라 상호보완 관계.

**hero/메타 톤 재작성 (2026-07-20) — 반영 완료**: "제품을 만든다"에서 "병목을 해결한다" 톤으로 사용자가 명시적으로 요청해 전면 반영함.
- hero tagline: "AI를 활용해 실제 문제를 빠르게 제품으로 만듭니다" → "AI로 현업의 반복업무와 병목을 찾아 없앱니다"
- hero lead: 마지막 문장("실행력을 0에서 1을 만드는 제품 개발로 확장")을 걷어내고, Emergency Backoffice/C++ 포팅(6개월→2개월) 사례를 구체적으로 언급하며 "반복업무와 병목을 AI로 없애는 데 집중" 톤으로 재작성. Morning Report Alpha는 "역량을 계속 검증" 정도의 보조 근거로 톤 하향.
- `<title>`, meta description/og/twitter, footer(4~7곳)에 남아있던 구 문구("AI로 문제를 제품으로 만듭니다" / "실제 사용 가능한 제품으로 만드는")도 전부 동일 톤으로 통일: title류는 "AI로 반복업무와 병목을 없앱니다", description류는 "현업이 실제로 멈추는 지점을 찾아내고, AI로 반복업무와 병목을 없애는 Ax Engineer"로 교체.
- grep으로 "제품으로 만듭니다" 잔존 문구 없음을 확인함 — 페이지 전체 톤이 이제 일관됨.

**세 번째 AI 활용 사례 — Redmine Local RAG PoC (2026-07-20)**: 사내 PMS(Redmine, ~10년 치 이력, 정형화 안 된 기록이라 검색 어려움)를 벡터 검색으로 찾을 수 있게 해보려던 개인 PoC. Emergency Backoffice·C++ 포팅과 달리 **프로덕션 미배포·개인 실험으로 종료**된 사례라는 점이 중요한 차이.
- 스택: Redmine Issues CSV 수동 export → JSON 변환 → 임베딩(`nomic-embed-text`, Ollama) → Qdrant 벡터 저장 → 로컬 LLM(`qwen2.5:3b`, Ollama) 질의응답, Docker Compose로 전체 구성. GitHub: https://github.com/dev-jhjoo/redmine-local-rag-poc (2026-05-17~18, 하루짜리 PoC)
- 로컬(Ollama) 선택 이유: 비공개 사내 데이터를 외부 AI API로 보내지 않기 위해 — Ax Engineer로서 데이터 보안을 고려한 판단 근거로 유효
- 한계(사용자 확인): (1) 이슈 제목만 임베딩해서 검색 정밀도 한계 뚜렷, (2) 조직적으로 로컬 LLM 상시 운영할 하드웨어 리소스 여력이 없어 도입 무산
- README 예시 질의문에 사내 고유명사("KShot", "3010 collector")가 노출되어 있었는데, 앞서 C++ 파일명 제외 요청과 같은 맥락으로 판단해 이력서/Notion 초안 모두에서 일반화된 예시로 대체함(자체 판단)

**반영 상태 (2026-07-20)**: 
- Notion 포스팅용 markdown 초안 작성 완료: `/Users/jeehoon/My/my-resume/docs/redmine-local-rag-poc-notion-draft.md` (수정 없이 확정)
- index.html 포트폴리오 탭에 2번째 카드로 반영 완료 (Morning Report Alpha와 동일 포맷: Problem/Hypothesis/MVP/My Role/Key Decisions/Current Result/Learnings/Next/Technology). `case__meta`를 "Product Case Study · PoC (미배포)"로 표기해 라이브 프로젝트와 구분. GitHub 링크만 제공(라이브 데모 없음), 스크린샷 없음(CLI 도구)
- 포트폴리오 탭 상단 소개 문구도 "운영하는" → "기획·개발한 사이드 프로젝트와 기술 검증(PoC)을"로 함께 수정해 PoC 포함을 반영

**포트폴리오 구성 최종 상태**: Morning Report Alpha(제품 오너십 증거, Live) + Redmine Local RAG PoC(Ax Engineer 정의에 가장 근접한 소재지만 미배포, PoC) 2개 카드 체제.

**How to apply**: 다음 대화에서 (1) 아직 미결인 case-grid 하이라이트 섹션 부활 여부, (2) 주석 처리된 스킬 섹션 재노출 여부는 사용자가 "패스"하기로 했으므로 재요청 전까지 먼저 꺼내지 말 것, (3) 다른 5개 회사(커넥틴, 카닥, 에이피엠멤버스, 에어프레미아, 엔에치엔케이씨피, 엑심베이)에는 AI 활용 이력이 없으므로 억지로 끼워넣지 말 것. 이번 대화 전반에 걸쳐 확립된 패턴 — GitHub/공개 자료로 먼저 조사 → 부족한 부분만 사용자에게 질문 → 초안 제시(민감 정보는 자체 판단으로 일반화) → 확정된 것만 반영 → 매 반영 후 커밋·푸시까지 이어가는 흐름 — 을 계속 따를 것.
