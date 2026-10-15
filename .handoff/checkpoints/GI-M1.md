# GI card — M1/M2 lesson-generation-review
As of: 2026-10-14 23:40 CDT · Artifacts: specs/M1-lesson-generation-review/decode.md@3785712, brief.md@3785712, docs/research/R01–R08@639bdbe, docs/product/prd.md@7f56978

## Summary (one screen)
Real ask (QB-1): show principal-level product judgment by building the review desk Newsela's curriculum staff would
use. An outline goes in. Standards-true lessons in Newsela's own lesson anatomy come out in the background. Reviewers
edit together, with AI help, and approve with an audit trail. Success is measured by reviewer minutes per lesson.
Problem: about 480 lessons per program (4 units × ~40 × grades 6–8) were written by freelancers. The CA State Board
votes in Nov 2026, and after that content can be revised only about every two years (R04, R05).
North Star (SC-001): median reviewer time from draft ready to approved, ≤ 60 min (aspirational).
Scope: M4 tracer = upload outline → drafts → edit → approve (US-1–3). M5 = AI assist, live co-editing, unit progress
(US-4–6). Later = approval checklist (US-7).
Research surprises: Program Type 1 = basic ELA K–8, which needs CCSS ELA alignment only (R01). The partner's outline
writes codes in a non-official spelling (W.6.2.c vs W.6.2c), and RL.6.9.a does not exist. FR-033 and FR-007 turn that
into a visible check, which makes a good demo moment.

## Decided for you (Type 2, reversible)
| D | Decision | Why | Reopen? |
|---|---|---|---|
| D1 | Partner material in gitignored docs/source/raw/ | uncleared; repo may go public | "reopen D1" |
| D2 | make check skips npm until package.json exists | real gate now, stack picked at GD | "reopen D2" |
| D3 | Research ran as 3 parallel agents, sources merged | 4x faster; merge fixed 1 dup S-id, 1 miscount | "reopen D3" |
| D4 | M4 tracer (US-1–3), M5 review power (US-4–6) | early try-it link | "reopen D4" |
| D5 | SC-001 ≤ 60 min, aspirational | no public baseline (R06) | "reopen D5" |

## Your decisions (Type 1 and human-only questions)
### 1. ⚠ Appetite and deadline
The brief says 1–2 days and shows no submission date. Recommended: 2 days of build after GD; deadline = the portal's
date, or "none set". Default: 2 days, US Central.

### 2. AI provider and spend cap (Type 1: spend)
| Option | Cost | |
|---|---|---|
| A Anthropic (Claude), cap $30 total, ≤ $0.50/lesson | you supply a key outside the repo | **recommended** (partner uses Claude Code; one unit ≈ 41 drafts ≈ $10–20) |
| B OpenAI, same cap | same | |
| Do nothing | no generation; the demo cannot run | |
Default: A.

### 3. ⚠ Partner material: may it be committed or quoted publicly? (U-01)
A keep it private and paraphrase (**recommended**, current state, D1) · B commit it. Default: A.

### 4. Who may approve a lesson? (Type 1: auth model; PRD A-2)
| Option | Cost | |
|---|---|---|
| A any signed-in reviewer approves; history records who | simplest; matches the brief's "review staff … approve" | **recommended** |
| B separate lead/approver role | +1 role, permission checks, more demo setup | |
| C two-person approval | slowest; hurts SC-001 | |
| Do nothing | approval cannot be trusted | |
Default: A.

### 5. ⚠ Generation scope (PRD open question, A-1, A-3)
Recommended: draft every numbered lesson type in the outline (Spark, Core Reading, Core Writing, Academic Discussion,
Showcase Writing), including ELD supports. Do not draft flex days or assessments. Default: as recommended.

### 6. ⚠ Unit drafting window (NFR-002)
Recommended: a 41-lesson unit is fully drafted within 60 minutes. Default: 60 min.

### 7. Repo and visibility (Type 1: visibility)
Per your kickoff recipe: a GitLab repo on labs.gauntletai.com plus a GitHub mirror. A public (**recommended**; partner
material stays out per D1) · B private until submission. I create and push only after your yes. Default: nothing is
created yet.

### 8. Email the partner's technical contact? (U-06, optional)
I would draft three questions for you to send: what "Program Type 1" means to them and whether ELD is in scope; the
code spelling and RL.6.9.a; their freelance review time per lesson. A yes, draft it (**recommended**) · B no.

### Confirm or change: PRD assumptions A-4 (lessons reference the novel by chapter and page), A-5 (WCAG 2.2 AA), A-6 (seeded fictional staff accounts for sign-in)
Default: confirmed.

## Skipped or reused
- audit-codebase: skipped (greenfield).
- Interviews inside decode/brief/PRD: parked into this card (WORKFLOW §4b).

Reply in one message, e.g. `1 default 2A 3A 4A 5 6 7A 8A`, or Revise / Stop. Next after your answer: `/plan-design`.
