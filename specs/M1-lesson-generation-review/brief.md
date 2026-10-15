---
milestone: M1
slug: lesson-generation-review
artifact: brief
written_by: sharpen-brief (software-factory-kit 0.2, inside /plan-product)
written_at: 2026-10-14 23:30 CDT (UTC-0500)
assignment: Newsela partner brief "Lesson Content Generation and Editing/Approval Workflow" v1, last updated 2026-10-12 (Gauntlet portal, held by the human); Newsela company panel (Gauntlet portal); sample unit outline G6 U3 (Google Sheet linked in the brief); example lesson G6 U1 L1 (Newsela CA review site linked in the brief)
track_recommended: Full
track_decided_in: "G0 row in .handoff/TRACKER.md ## Approvals; this brief holds only the recommendation"
problem_allowlist: Newsela
gate: G0
---

# M1 brief: Newsela Lesson Studio — generate, review and approve a unit of lessons

## Ask

> Newsela's curriculum review staff need a tool that turns a unit outline into draft lessons and lets them edit and approve those lessons together, within a 1–2 day build.

The human's original words: "find the newsela project, scrape the company info and company project and read through the attachement and lets start their project with our new ai workflow on the new branch"

## Problem

- (paraphrase, U-01) Entering California "Core" instruction means full-year programs: four sequential units of about forty 50-minute lessons each, for each of grades 6–8 — brief §PRD.
- (paraphrase, U-01) Lessons have traditionally been written by a large pool of freelance writers; this is slow, needs heavy coordination, takes very long and has quality problems, and staff then review, revise and import piles of lesson documents — brief §Business context.
- (paraphrase, U-01) Doing this by hand is "prohibitively enormous" work and is the barrier to entering the market — brief §PRD, §Business context.
- (paraphrase, U-01) Review staff must be able to review, update and approve each lesson, and the approval process must be rigorous — brief §Business context.
- (paraphrase, U-01) Lessons must align to the specific state standards each outline row names, using the named reference text — brief §Functional requirements.

**Restated, no solution or tech words:** Newsela's curriculum staff must produce and sign off hundreds of standards-aligned lessons per grade before they can sell a full-year program. Today each lesson is drafted by a freelance writer, then reviewed, revised and re-entered by staff, which is slow, hard to coordinate and uneven in quality. Doing nothing keeps the full-year market out of reach.

- **Who has it:** instructional designers who write unit outlines; review staff (20+) who check, revise and sign off lessons.
- **What they do today instead:** commission freelance writers per lesson, collect documents, review and revise them, then import them by hand.
- **Cost of doing nothing:** a market the partner sizes in the tens of millions of annual recurring revenue stays closed (brief §Impact metrics); every program costs months of coordination.

## Job stories

| ID | When… | I want… | so I can… | Who | Source |
|---|---|---|---|---|---|
| JS-01 | When I have finished a unit outline of about forty lessons | to get a first draft of every lesson without commissioning writers | spend my time judging lessons instead of waiting for them | instructional designer | REQ-01, REQ-08 |
| JS-02 | When a drafted lesson lands in my queue | to see at once which standards, texts and minutes it covers and whether it matches our lesson anatomy | catch structural or alignment problems in seconds | reviewer | REQ-02, REQ-03, REQ-07 |
| JS-03 | When a lesson is mostly right but a section is weak | to rewrite or regenerate just that part with help, in place | fix it without redoing the whole lesson | reviewer | REQ-05 |
| JS-04 | When several of us are working through the same unit | to edit alongside colleagues without overwriting each other | keep twenty reviewers moving in parallel | reviewer | REQ-09, REQ-11 |
| JS-05 | When I am satisfied with a lesson | to mark it complete with a record of who signed off and when | trust that approved lessons stay approved and the unit's progress is visible | reviewer / lead | REQ-06 |
| JS-06 | When I check on a unit | to see how many lessons are drafted, in review and approved | know whether the program will be ready on time | lead | REQ-06, REQ-13 |

## Hiring partner

| Aspect | What we know | Source | What the project should show them |
|---|---|---|---|
| Who they are | EdTech, 201–500 employees, engineering team 51–100; helps teachers and districts through leveled content plus assessment, data and intervention tools with AI assistance | company panel §About | A tool that fits their content-operations reality, not a toy |
| Stack | TypeScript/JavaScript, Python; MySQL, Postgres, MongoDB, Elasticsearch; React, Next.js; REST; Node.js; AWS; Kafka; agents and LLM APIs | company panel §Technical stack | Stay inside it (see REQ-11) |
| Working style | Async/remote-first; high autonomy 4/5; ambiguous problem solving 5/5; cross-functional 4/5; rapid feature delivery and iteration; mixed greenfield and legacy | company panel §Engineering environment | Decide sensibly under ambiguity and say why; ship fast with clean structure |
| Role | Principal Product Engineer / Member of Technical Staff | brief header | Product judgment: workflow design and metrics, not only code |
| Hiring | 3–4 interview rounds, no coding assessment; week 6 interview access | company panel §Interview process | Docs and demo that let them grill design tradeoffs |
| Products and CA Core plans | ⚠ (→ R03) | — | — |

## Value and metrics

- **Underlying problem in the business's terms:** (paraphrase, U-01) manual lesson writing is "prohibitively enormous" work that blocks a market worth "10's of millions" of ARR — brief §PRD, §Impact metrics.

| ID | Candidate metric | Role | Actionable or vanity ("if bad, what would we fix?") | Leading or lagging | Data that would measure it |
|---|---|---|---|---|---|
| NS-01 | Reviewer time per lesson from "draft ready" to "approved" | North Star | actionable: if high, fix generation quality or review tooling for the slowest sections | lagging | status-change timestamps per lesson (⚠ baseline for freelance flow → R06) |
| SM-01 | Share of lessons approved with light edits (small change from the generated draft) | explains NS-01 (draft quality) | actionable: low share → improve prompts/structure for those lesson types | leading | draft vs approved content diff per lesson |
| SM-02 | Share of generated lessons that pass automatic structure and standards checks on first try | explains NS-01 | actionable: failures name the broken section or unknown standard | leading | generation validation results |
| SM-03 | Approved lessons later reopened for a content problem | guards NS-01 (rushing approvals to look fast) | actionable: high → tighten the approval checklist | lagging | reopen events per lesson |

Vanity traps considered and rejected: lessons generated (counts output, not usable lessons); tokens used (cost
context only); editor sessions opened (activity, not progress).

## Appetite and deadlines

- **Now:** 2026-10-14 23:30 CDT (UTC-0500)
- **Appetite:** ⚠ your chosen time to spend (→ G0); the partner brief sets "1–2 days" (brief §Time constraints)
- **Timebox:** ⚠ start → end (→ G0)

| Checkpoint | As written in the source | Local time (converted by date) | Source |
|---|---|---|---|
| Build time | "1-2 days" | ⚠ timezone? and start date (→ G0) | brief §Time constraints |
| Submission | none shown on the portal page | ⚠ submission deadline and timezone? (→ G0) | portal project page |

## Spec is law

Sources read in full: partner brief (all sections, 1 page), company panel (all sections), sample unit outline (57
rows, 16 columns), example lesson (all sections expanded). Requirements extracted: 15. Second pass: 1 new row added
(REQ-15).

| ID | Requirement (verbatim; uncleared source: `(paraphrase, U-##) <text>`) | Source | Deliverable (assignment's exact filename, or observable proof) | Owning phase / skill | Due | Status |
|---|---|---|---|---|---|---|
| REQ-01 | (paraphrase, U-01) Generate lessons from an uploaded or imported unit outline (a spreadsheet of ~40 lessons, each with coverage and learning arc) | brief §Functional req. 1 | demo: outline in → lessons drafted | 3 write-prd → 9 implement-task | build end | mapped |
| REQ-02 | (paraphrase, U-01) Generation is knowledgeable about CA Common Core ELA "Program Type 1" standards for grades 6–8 | brief §Functional req. 1 | lessons cite only real standards with their definitions | 3 write-prd (+ R01) | build end | mapped |
| REQ-03 | (paraphrase, U-01) Each lesson is about 50 minutes of instruction, teaching the CA ELA/ELD standard codes named in the outline, using the named reference text | brief §Functional req. 1 | lesson pacing totals 50 min; standards and text match the row | 3 write-prd | build end | mapped |
| REQ-04 | (paraphrase, U-01) Import generated lessons into a system for persistence | brief §Functional req. 2 | lessons survive restart | 3 write-prd → 5 design-hld | build end | mapped |
| REQ-05 | (paraphrase, U-01) UI/UX to review and edit a lesson's content (WYSIWYG) with AI-assisted tooling as helpful | brief §Functional req. 3 | demo: reviewer edits with AI help | 3 write-prd → 4 map-ux-flows | build end | mapped |
| REQ-06 | (paraphrase, U-01) Approval workflow: once reviewed/updated a lesson is flagged complete | brief §Functional req. 4 | demo: approve → status complete | 3 write-prd | build end | mapped |
| REQ-07 | (paraphrase, U-01) Follow the example lesson's format and structure (other examples may be browsed) | brief §Functional req. 6 | generated lesson has the example's sections | 3 write-prd (+ R02) | build end | mapped |
| REQ-08 | (paraphrase, U-01) Generation can run asynchronously after an outline is uploaded; a few minutes per lesson is fine | brief §Performance | NFR in PRD | 3 write-prd | build end | mapped |
| REQ-09 | (paraphrase, U-01) Loading and editing performant for 20+ reviewers | brief §Performance | NFR in PRD | 3 write-prd (+ R05) | build end | mapped |
| REQ-10 | (paraphrase, U-01) Clean, well-structured architecture | brief §Code quality | `docs/architecture/hld.md`, `lld.md` | 5 design-hld, 6 design-lld | build end | mapped |
| REQ-11 | (paraphrase, U-01) Languages: JavaScript (Next/Node), React, optional Python; AI via OpenAI or Anthropic APIs; ProseMirror and Yjs for the collaborative editor | brief §Technology | constraint rows in PRD | 3 write-prd (Constraints) → 5 design-hld | build end | mapped |
| REQ-12 | (paraphrase, U-01) Deliverables: source code, technical documentation, demo video | brief §Submission | repo URL; `README.md` + `docs/`; demo video | 14 garden-docs, 17 write-demo-script, 18 record-demo (+ U-04, U-05) | ⚠ submission deadline (→ G0) | mapped |
| REQ-13 | (paraphrase, U-01) Thoughtful design and an easy to understand/use/navigate workflow; creativity to raise internal staff productivity | brief §"Off-limits tech" field | demo + SC in PRD | 3 write-prd, 4 map-ux-flows | build end | mapped |
| REQ-14 | (paraphrase, U-01) Time constraint 1–2 days | brief §Time constraints | appetite | G0 | — | ⚠ your appetite (→ G0) |
| REQ-15 | (paraphrase, U-01) AI usage documentation is optional | brief §Submission | `docs/AI_USAGE.md` (optional) | 14 garden-docs | build end | mapped |

Conflicts between sources: the sample outline's title says Unit 4 while its file names say Unit 3; not a requirement
conflict, recorded as an import edge case (decode T-4).

## User-owned steps

| ID | Step | Why only the human | Due | Blocks |
|---|---|---|---|---|
| U-01 | May the brief quote the partner brief, sample outline and example lesson word for word, and may a copy be committed? ⚠ confidential? (→ G0) | partner relationship | GI | all quoting; recommended: no, keep in gitignored `docs/source/raw/` |
| U-02 | Choose AI provider and supply its key outside the repo; set a spend cap | money, account | before the first build milestone | generation (REQ-01) |
| U-03 | Create the GitLab repo + GitHub mirror and decide visibility; approve each push | account, visibility | before first push | CI, MR |
| U-04 | Approve deploys to a public host (and pay if needed) | money, account | GT of the first build milestone | try-it link, demo |
| U-05 | Record and upload the demo video; submit on the Gauntlet portal | face/voice, account | ⚠ submission deadline (→ G0) | REQ-12 |
| U-06 | Optionally email the partner's technical contact with clarifying questions | relationship | GI | ⚠ open scope questions |

## Track

**Recommended: Full**, because WORKFLOW.md §3: a new product (no PRD exists) is Full; a graded partner project is always Full.
Greenfield or brownfield: greenfield.
Track announced by the supervisor: Full (TRACKER Log 2026-10-14 23:25 CDT ROUTE M1).
Existing PRD: none.

| Option | What you get | What it costs, in plain words | Fits this ask? |
|---|---|---|---|
| Full | Every phase from this brief to ship, with three checkpoints (GI, GD, GT) | about 2–3 hours of planning before code; most of it runs without you | yes: new product, graded, interview defense |
| Standard | Starts from an existing PRD | nothing to start from | no: no PRD exists |
| Fix | One failing repro, smallest fix | not applicable | no |
| Do nothing | No build | partner project stays unsubmitted | no |

## Research questions

| ID | Question | Decision it unblocks | Answered when | From |
|---|---|---|---|---|
| R01 | What is the canonical, citable source for CA CCSS ELA/Literacy grades 6–8 and CA ELD standards (codes + definitions), and what does "Program Type 1" mean in California's ELA/ELD adoption? | REQ-02, REQ-03; how standards are known to the product | an official CDE source lists codes and text, and an official source defines Program Type 1 | REQ-02 |
| R02 | What sections and lesson types make up a Newsela CA lesson (Spark, Core Reading, Core Writing, Academic Discussion, Showcase Writing, Flex), and which parts are fixed vs varying? | REQ-07; lesson anatomy FRs | at least two lesson types inspected on the partner's review site | REQ-07, JS-02 |
| R03 | Who is the partner — products, customers, CA Core curriculum plans, what roles they hire for? | Hiring partner section; demo framing | partner's own site/press/job posts read | Hiring partner ⚠ |
| R04 | What is the market — California's ELA instructional-materials adoption timeline, incumbents, ideal customer (which districts) and market size? | SC targets, North Star framing | official adoption schedule + a sized estimate with formula | REQ-14 context, NS-01 |
| R05 | What is the usage and load profile — lessons per program, reviewers, review cadence and peak concurrent editors per lesson/unit? | NFRs for REQ-09 | arithmetic from brief + any public review-process data | REQ-09 |
| R06 | What data could measure reviewer time-to-approve, and what is the baseline time/cost for freelance-written lessons? | NS-01 target | a public benchmark for curriculum writing time or cost per lesson | NS-01 |
| R07 | How much of a copyrighted anchor text may lesson materials quote, and how do published curricula reference novels? | FR on excerpts | an authoritative fair-use or publisher-practice source | decode T-3 |
| R08 | What published quality criteria for ELA instructional materials (e.g. state or independent review rubrics) could act as a review checklist? | approval checklist FRs, SM-02 | an official or widely used rubric read | REQ-06, REQ-13 |

## Parking lot

| ID | Idea (verbatim) | Raised by | When | Need behind it |
|---|---|---|---|---|
| P-01 | "prompts/agent knowledgeable on CA Core ELA Program Type 1 standards" | assignment | 2026-10-12 | JS-02 |
| P-02 | "any lighter-weight hosting platform, e.g. Vercel or Railway, works then feel free" | assignment | 2026-10-12 | U-04 |
| P-03 | "we typically use Claude Code and Codex" | assignment | 2026-10-12 | none: context on the partner's tooling |

## Interview log

One question at a time, each with a recommendation; answers verbatim. Pass 1, 2026-10-14.

| Q# | Question | Recommended (and why) | Answer (verbatim) | Landed in |
|---|---|---|---|---|
| — | none asked: /plan-product parks human-only questions for the batched GI card (WORKFLOW §4b) | — | — | ⚠ rows above |
