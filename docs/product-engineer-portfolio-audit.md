# Product Engineer Portfolio Audit

- Repo: `my-resume` (single static site, no framework)
- Reviewed: `index.html`, `assets/portfolio-img.png`, git history, prior agent memory
- Date: 2026-07-11

## 1. What the repo actually is

- **No build system.** `index.html` is a single self-contained file (~1,570 lines): inline `<style>`, inline `<script>`, no npm/package.json, no CSS/JS framework. It renders correctly served as a static file (verified with a local HTTP server — 200 OK, content matches file).
- **Client-side tab app.** A `.topbar` tab bar toggles three `.view` sections by `data-view`: `resume` (이력서), `cv` (경력기술서), `portfolio` (포트폴리오). State is stored in `location.hash`, so `#resume`, `#cv`, `#portfolio` are the site's only routes/anchors.
- **Shared hero.** One hero block (name, tagline, lead paragraph, contact chips, 4-stat bar) sits above all three tab views and does not change per tab.
- **Print support.** `@media print` rules exist for PDF export (a "PDF 저장" button calls `window.print()`), and all three views are forced visible for print. Any hero/case-study markup changes must keep this working.
- **No lint/build/test tooling exists.** There is nothing to `npm run lint/build/test` — validation for this project means: valid HTML, working tab/theme/print JS, and visual/responsive review.

## 2. Current positioning

- `<title>`: "주지훈 | Backend Engineer · FDE / Internal Tools Focus"
- Hero tagline: "현업의 병목을 찾아, 문제를 정의하고 해결합니다"
- Hero lead: emphasizes multi-domain backend experience (결제/커머스/항공/메시징), production incident response, and "자동화 서비스를 직접 구축" — but frames all of it as an extension of backend/운영 execution, not product discovery.
- Footer and topbar brand label repeat "Backend Engineer" / "FDE / Internal Tools Focus".
- Hero stat bar: `9년+ 백엔드 개발·운영 경험`, `300만+/일 메시지 유통 시스템`, `60억+ 상품권 판매·정산 운영 규모`, `10+ 외부 시스템·API 연동` — all infra/ops-scale metrics, zero product/user-facing metrics.

**Git history context** (relevant, not to be repeated verbatim in the site): the site was already repositioned once toward "FDE / Internal Tools Focus" (commit `c446014`, 2026-07-05), including a dedicated "대표 문제 해결 사례" (featured case studies) section covering Emergency Backoffice + Morning Report Alpha. That section was later **removed** (commits `fd340ef`, `ccf1be4`) and the current portfolio tab was simplified back down to a single project card. The CSS for that removed section (`.case`, `.case__meta`, `.case-result`, `.case-grid`) is still in the stylesheet but unused in the body — dead code, but directly reusable for the new Product Case Study (see Plan doc).

Prior agent memory also records an explicit user preference: **large resume edits should be preceded by an analysis/agreement step, not done directly.** This task's required Inspect → Audit → Plan → limited-implementation sequence already satisfies that.

## 3. Content worth preserving as-is

- All employment dates, titles, and company names — no inconsistencies found across hero, resume, and cv views.
- Quantified facts that are already stated in the source (not to be touched, not to be inflated further): 9년+ 경력, KP모바일 일 250~300만 메시지, APM멤버스 가입자 약 1.7만 명·가맹점 약 1천 개·상품권 누적 판매 60억 원·정산 50억 원(2022.11 기준), 약 60만 개 MMS 파일 이전.
- The "일하는 방식" (Working Principles) pillars in the resume view already read close to product-engineer language ("문제를 기능보다 먼저 정의합니다", "빠르게 만들되 운영 가능하게 만듭니다") — good raw material, low risk to reuse language/tone from here in the hero rewrite.
- Morning Report Alpha's existing copy already contains real MVP/trade-off reasoning ("무료 인프라로 구성한 자동화": GitHub Actions cron, CSV+git as a database substitute, Cloudflare static hosting) — this is genuine product-engineering evidence (scrappy MVP decision-making) that just isn't labeled as such yet.
- Print layout, theme toggle, accessible tab markup (`role="tablist"`, `aria-selected`) — functional, no reason to touch.

## 4. Backend-heavy / technology-first content

- Resume "경력" bullets and CV "기여 포인트" are still written tech-stack-first in several places (e.g., "Bucket4j 기반 TPS 제어, Netty 비동기 이벤트 드리븐 통신을 적용" leads with implementation detail before the operational problem it solved). Out of scope to rewrite this round (Experience section is explicitly excluded from this task), but flagged for a future pass.
- "기술과 실행 범위" skill panels are grouped by technology category (Backend & Integration / Data & Automation / Operations & Resilience / Infra & Delivery) rather than by capability-for-product-outcome. Also out of scope this round.
- Hero stat bar (see above) is 100% infra-scale, 0% product/user impact — a Product Engineer recruiter skimming the hero currently sees no evidence of product thinking at all. This is in-scope since it lives inside the hero section.

## 5. Missing product evidence

- No section anywhere frames a project using Problem → Hypothesis → MVP → Decision → Result → Learning → Next. All existing project/job content is feature-list or responsibility-list style.
- Morning Report Alpha has no stated **problem/who-had-it**, no stated **hypothesis**, no **usage evidence** (no user, no personal-usage cadence claim beyond "자동 실행"), no **learnings**, no **next iteration**. These must be added carefully — real where derivable from existing copy, `[TODO]` where not.
- No visible artifacts for the other product-oriented projects referenced in the agent brief (WishLamp, hair-exam quiz service, route-planning MCP, AI Product Lab / "100 AI Products"). These cannot be added without factual confirmation — see open TODOs below.
- No "How I Build" process section exists (out of scope this round, but a gap worth flagging for the plan).

## 6. Information requiring user confirmation (do not fabricate)

1. Do the WishLamp, hair-exam quiz (Cloudflare Pages), and route-planning MCP projects actually exist in a shareable state (live URL, repo, or at least a concrete build summary)? None currently appear in the repo.
2. Is there an "AI Product Lab" / "100 AI Products" initiative the user wants represented, and if so, at what stage (idea vs. building vs. shipped)?
3. Morning Report Alpha: any real usage signal beyond "GitHub Actions runs it on schedule" (e.g., how long it's been running, whether the user actually reads/acts on the Telegram reports, any accuracy/output-quality observation)? None is currently stated in the source; will not be invented.
4. Morning Report Alpha: what, if anything, is the actual "next iteration" plan (more tickers, alerting channels, backtesting the signal, etc.)? Not currently stated.
5. Should "FDE / Internal Tools Focus" remain as a secondary/parallel positioning line, or should Product Engineer fully replace it in `<title>`, meta tags, topbar brand label, and footer? (Agent brief lists FDE as one of several target role types alongside Product Engineer, so full removal is not required — but the current site literally puts "FDE / Internal Tools Focus" as the *only* subtitle, which the plan proposes changing.)

## 7. UX / IA issues

- Hero has no CTA/jump links to the tab sections — a recruiter lands on hero copy and stat bar with no explicit next action beyond the topbar tabs (which are easy to miss as a mechanism at a glance).
- The single portfolio card currently mixes "feature list" and "infra rationale" under generic headers (`핵심 기능`, `무료 인프라로 구성한 자동화`) rather than a problem-first case-study structure a Product Engineer reviewer expects.
- Portfolio tab has only one entry, so there is currently no "Featured Products" (multiple, scannable) layer distinct from a deep-dive case study — both are collapsed into one card. Acceptable for this round (only one verified product exists) but worth noting for the plan's IA section.

## 8. Technical debt / constraints affecting implementation

- No CSS/JS module system — all changes must be made directly inside the single `index.html`, keeping the existing inline `<style>`/`<script>` conventions (do not introduce a build step; that would be a bigger decision requiring separate user sign-off).
- Reusable-but-dead CSS classes (`.case`, `.case__meta`, `.case-result`) exist from the previously removed case-study section and can be revived rather than adding new styles — reduces risk and diff size.
- `@media print` rules must continue to work after hero/case-study markup changes (verify visually/structurally, since there's no automated test).
- `assets/portfolio-img.png` is the only project screenshot asset available; no other product screenshots exist yet.
