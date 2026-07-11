# Product Engineer Rebranding Plan

Companion to `docs/product-engineer-portfolio-audit.md`. This plan covers the full target information architecture, but **only the Hero rewrite and one Product Case Study are implemented in this pass** (see §7 "This iteration's scope"). Everything else is a roadmap for future iterations, not a promise of what changes today.

## 1. New positioning

Primary line (Korean-first, matches agent brief):

> AI를 활용해 실제 문제를 빠르게 제품으로 만드는 Product Engineer

Supporting line, grounded in this candidate's actual history (backend depth + first shipped AI-assisted product):

> 백엔드와 운영 경험을 기반으로 문제를 정의하고, MVP를 설계하며, 실제 사용 가능한 제품으로 구현합니다.

Positioning rules for this and future passes:
- Backend/ops depth stays visible — it is the credibility base, not something to hide.
- **Decided (2026-07-11): FDE positioning is fully removed**, not kept as a secondary descriptor. Confirmed zero remaining "FDE" occurrences anywhere in `index.html` after this change.
- No new metrics, users, revenue, or timelines are introduced anywhere. Every number in the rewritten hero/case-study must already exist in the source file.

## 2. Target audience

- Product Engineer / 0→1 product-track recruiters and hiring managers
- Startup founders hiring a generalist builder
- Forward Deployed Engineer / AI Solution Engineer teams
- Engineering managers and senior backend reviewers who need to see the technical depth is real, not diluted

The hero and case study must read as credible to the last group even while speaking to the first three — no buzzword inflation.

## 3. Target site information architecture (full roadmap)

Current: Hero (shared) → Tabs [이력서 / 경력기술서 / 포트폴리오]

Target (phased — not all built this iteration):

1. **Hero** — Product Engineer positioning, one-line + supporting paragraph, contact row and stat bar kept as-is (already factual, still useful as backend-credibility signal). **Decided (2026-07-11): no hero CTA row.** A CTA row was prototyped (links into `#portfolio`/`#resume`/`#cv`/`mailto:`) but the user asked for it to be removed — the topbar tabs remain the only navigation into the three views. Do not re-add a hero CTA row without a new explicit request.
2. **Featured Products** *(decided excluded)* — currently only one verified product exists (Morning Report Alpha); stays a single card. WishLamp / hair-exam quiz / route-planning MCP will **not** be added — user confirmed (2026-07-11) to exclude these.
3. **Product Case Studies** *(this iteration: 1 of N)* — deep-dive using Problem / Hypothesis / MVP / Key Decisions / Current Result / Learnings / Next / Technology. Lives inside the existing `#portfolio` tab (no new tab needed yet — only one case study exists).
4. **Experience** *(partially done 2026-07-11)* — `#resume` 탭의 "경력" job 불릿을 문제→행동→임팩트 순서로 재구성 완료(모든 회사, 7곳). 날짜/수치/태그/회사명은 전혀 변경하지 않음. `#cv`(경력기술서) 탭의 회사별 상세 story 카드는 아직 미착수 — 다음 후보.
5. **How I Build** *(future)* — new section, not built this round.
6. **AI Product Lab** *(decided excluded — still too early)* — user confirmed (2026-07-11) the initiative is at too early a stage to represent on the site. Do not build this section until the user says otherwise.
7. **Writing / Build Log** *(future)* — no source content currently exists for this.
8. **Resume / CV** *(future, light touch only)* — `#resume`/`#cv` content itself is unchanged this round; only the shared hero above them changes.

## 4. Content migration plan (this iteration only)

| Current | Action | Destination |
|---|---|---|
| `<title>` / meta description / og / twitter tags | Rewrite copy to lead with Product Engineer positioning, keep backend depth | `<head>` |
| Topbar brand label ("주지훈 · Backend Engineer") | Update subtitle to reflect Product Engineer + backend, keep short | `.topbar .brand` |
| Hero `h1` sublabel, `.tagline`, `.lead` | Rewrite per §1 | `.hero` |
| Hero contact row | Unchanged | `.hero .contact-row` |
| Hero CTA | Prototyped then **removed per user decision (2026-07-11)** — no CTA row in the hero | — |
| Hero stat bar | Unchanged (already factual) | `.stats` |
| Footer text | Update to match new positioning line | `.footer` |
| Portfolio card for Morning Report Alpha (`핵심 기능`, `무료 인프라로 구성한 자동화` blocks) | Restructure into Product Case Study template (§5), preserving every existing factual sentence — no content deleted, only re-labeled/re-ordered, with TODOs added where the template asks for something not yet stated | `#view-portfolio .portfolio-card` |
| `#resume` 경력(Experience) job 불릿 7개사 | 문제→행동→임팩트 순서로 재작성. 같은 문서(CV 탭)에 이미 존재하는 사실(예: 케이피모바일의 기존 SQL 기반 TPS 제어/Socket 통신)만 문제 맥락으로 끌어옴 — 새로운 사실 추가 없음. 날짜/수치/태그 불변 | `#view-resume .job` |

`기술과 실행 범위`(skill panels), `일하는 방식`(pillars), CV 탭 회사별 story 카드는 이번에도 미변경.

## 5. Product Case Study: Morning Report Alpha — content plan

Mapped from existing verified copy (no invented facts), using the template from the agent brief. Reuses the dormant `.case__meta` / `.case-result` CSS classes noted in the audit instead of adding new styles.

- **One-line summary** — reuse/tighten existing intro sentence ("외부 데이터 수집 → AI 분석 → 저장 → 대시보드 → 알림을 하나의 운영 가능한 워크플로로 연결한 개인 프로젝트").
- **Problem** — derivable from existing framing (개인이 여러 뉴스/시세 소스를 매일 수동으로 확인해야 하는 부담) but the *specific* personal trigger isn't stated in source → write conservatively, mark the specific origin story as `[TODO: 프로젝트를 시작하게 된 구체적 계기 확인]`.
- **Hypothesis** — not explicitly stated in source. Draft a reasonable inference from what was built (예: "시장 개장 전 뉴스·가격 데이터를 구조화해 보여주면 판단에 드는 시간을 줄일 수 있을 것") but mark as `[TODO: 실제 가설 문구 확인/수정]` since it's inferred, not quoted.
- **MVP** — fully supported by existing content: Google News RSS + Yahoo Finance 수집, Gemini 2.5 Flash-Lite Structured Output, CSV/JSON 이력 저장, Cloudflare 정적 대시보드, Telegram 알림, GitHub Actions 스케줄링. No invention needed.
- **My Role** — supported: 개인 프로젝트로 기획·개발·운영 전체를 직접 수행 (기존 "직접 기획·개발·운영하는 사이드 프로젝트" 문구 근거).
- **Key Decisions** — fully supported by existing "무료 인프라로 구성한 자동화" block: DB 없이 CSV+git commit으로 이력 관리, 서버 없이 GitHub Actions cron + Cloudflare 정적 호스팅으로 무료 운영. This is genuine MVP trade-off reasoning already in the source — just needs the "why" made explicit (cost/simplicity over infra ownership).
- **Current Result** — only verifiable claim is operational status (자동 수집·분석·배포·알림이 스케줄대로 동작 중, 라이브 대시보드 공개). No user/accuracy/engagement metric exists → explicitly write "현재 개인용으로 운영 중" and mark `[TODO: 실사용 빈도, 피드백, 정확도 등 있으면 추가]` rather than imply broader adoption.
- **Learnings** — one defensible, non-metric learning can be stated: 무료 인프라만으로 수집→분석→배포→알림까지 하나의 파이프라인을 끝까지 운영 가능한 형태로 만들 수 있음을 확인. Anything beyond this (e.g., data quality issues, model accuracy observations) → `[TODO: 운영하며 배운 점 추가 확인]`.
- **Next** — not stated in source → `[TODO: 다음 개선/실험 계획 확인 (예: 종목 확대, 백테스트, 알림 채널 추가 등)]`.
- **Technology** — unchanged list, moved to the end per template rule (technology listed last, not leading).

## 6. Component changes

- No new CSS files/build step. All changes inline in `index.html`'s existing `<style>` block.
- Revive `.case__meta` (small eyebrow/status label) and `.case-result` (accent callout box) for the case study — currently defined but unused (audit §1/§8).
- No hero CTA styles — prototyped (`.hero-cta`, `.cta-link`, `.cta-link--primary`) and then removed per user decision; the tab-switching JS was reverted to its original `.tab`-only form (the `[data-view]` generalization added to support CTA anchors was removed along with them).
- No changes to theme JS or print JS beyond the CTA-related additions being reverted — only markup/copy inside existing containers.

## 7. This iteration's scope (what actually gets implemented now)

In scope:
1. Hero positioning rewrite: `<title>`, meta/OG/Twitter description, topbar brand subtitle, `h1` sublabel, `.tagline`, `.lead`, footer line. Stat bar values unchanged. No hero CTA row (removed per user decision).
2. Convert the Morning Report Alpha portfolio card into a full Product Case Study per §5, with `[TODO: ...]` markers for anything not already verifiable from source content.

Explicitly out of scope (do not touch): Experience/경력 bullets and CV company breakdowns, 기술과 실행 범위 skill panels, 일하는 방식 pillars, any new sections (Featured Products grid, How I Build, AI Product Lab, Writing/Build Log), any new routes/tabs.

## 8. Open factual TODOs

Resolved by user on 2026-07-11:
- ~~WishLamp / hair-exam quiz / route-planning MCP~~ — **excluded**, will not be added to the site.
- ~~AI Product Lab / "100 AI Products"~~ — **excluded for now**, still too early-stage to represent.
- ~~FDE positioning~~ — **fully removed**, confirmed zero occurrences in `index.html`.
- ~~Morning Report Alpha — origin trigger~~ — resolved: 최근 주식 시장 활황 대비 본인 지식 부족을 느껴, AI로 투자 심리를 분석해보고 싶었던 개인적 동기. Written into the Problem block.
- ~~Morning Report Alpha — hypothesis~~ — resolved: "종목별 뉴스 기사 분석 점수와 실제 시장 가격의 움직임이 비슷할 것이다." Written into the Hypothesis block, replacing the earlier inferred draft.
- ~~Morning Report Alpha — usage signal/accuracy~~ — resolved as "still in progress, not yet measured" (빈도·피드백·정확도 검증 진행 중) — not a fabricated number, an honest status. Written into the Current Result block.
- ~~Morning Report Alpha — learnings~~ — resolved: added that AI 자동화에는 분석 실패·타임아웃·rate limiting 같은 돌발 상황에 대한 세심한 예외 처리가 필요하다는 학습. Appended to the Learnings block.
- ~~Morning Report Alpha — next iteration~~ — resolved: 약 한 달간 데이터 수집·결과 확인 후 실제 투자 여부 판단. Written into the Next block.

No open factual TODOs remain in the Morning Report Alpha case study as of 2026-07-11. The `.todo-flag` CSS utility stays in the stylesheet (unused for now) for reuse if a future case study needs to visibly flag unconfirmed content.
