---
id: R06
question: "What data could measure reviewer time-to-approve, and what is the baseline time/cost for freelance-written lessons?"
asked_in: specs/M1-lesson-generation-review/brief.md#research-questions
unblocks: "NS-01 target"
answered_when: "a public benchmark for curriculum writing time or cost per lesson"
status: partial
confidence: medium
supersedes: none
date: 2026-10-14
budget: 12/15 tool calls
researched_by: Claude Code, claude-opus-5-5
---

# R06 Measuring time-to-approve and the freelance lesson baseline

## Answer

Reviewer time-to-approve can be measured from per-lesson status-change timestamps (draft ready, first opened,
approved) plus editing activity, all of which the product records itself; Newsela publishes no baseline for its
freelance flow. Public benchmarks give an hourly cost, not a per-lesson one: freelance K-12 curriculum writing runs
about $50–65/hour (primary) and $80–115/hour (secondary) in the EFA's 2026 survey, and US instructional coordinators
earn a median $37.23/hour (BLS, May 2025); no source read states hours per lesson, so cost per lesson is an inference
with a wide range (about $100 to $2,300). Confidence: medium, because only the BLS wage is Tier A and hours per lesson
is unsourced. (S05.1, S06.1, S06.3)

## Takeaway

The app can time every review itself from its own status changes, but nobody publishes how long a freelancer takes
to write one lesson, so any "before" number is an estimate until Newsela shares its own.

## Findings

- **F1** [LB] Review staff must review, edit and approve each lesson, and approval flags the lesson complete in the system (paraphrase) — S05.1 (A), partner brief (portal) §Functional requirements item 4 and §Business context
- **F2** [LB] Today lessons are written manually by a large pool of freelancers, which the partner calls slow, heavy on coordination and quality-problematic; the brief gives no hours, cost or turnaround figure (paraphrase) — S05.1 (A), partner brief (portal) §Business context
- **F3** The EFA 2026 Rate Chart lists curriculum development at $50.00–65.00/hour for primary school curricula (5–25¢/word) and $80.00–115.00/hour for secondary school curricula; it has no lesson-plan row — S06.1 (B, single publisher, so not load-bearing alone), the-efa.org/rates, Writing › Curriculum Development
- **F4** The EFA rates come from a survey run November 2025 to mid-January 2026 with over 1,100 respondents, open to members and non-members, and are "for guidance only and are not mandated or recommended rates" — S06.2 (B, same publisher as S06.1), 2026-03-24 release
- **F5** [LB] Instructional coordinators, who design curricula and evaluate instructional materials, earned a median $37.23 per hour ($77,440 per year) in May 2025 — S06.3 (A), BLS Occupational Outlook Handbook, Pay
- **F6** Practitioner surveys put corporate instructor-led training at 30–80 (2003) and 49–89 (2009) development hours per hour of instruction — S06.4 (C, colour only), karlkapp.com 2009 update
- **F7** The brief's own metric plan already names status-change timestamps per lesson as NS-01's data source, and draft-vs-approved diffs and reopen events for SM-01 and SM-03 — brief.md §Metrics (project's own document, not an external source)

## Inferences

- **I1** from F1 + F7: what measures time-to-approve. The product can log, per lesson, `draft_ready_at`, `first_opened_at`, `approved_at`, approver id, and a reopen event; elapsed time = `approved_at − draft_ready_at` (includes queue wait) and hands-on time ≈ `approved_at − first_opened_at` or summed active-edit intervals from the times of editor updates (excludes idle). High confidence it is measurable; which of the two NS-01 uses is a PRD choice.
- **I2** from F3 + F5: hourly cost range for a lesson writer. Formula: cost per hour taken directly from sources. Assumptions: A-1 grades 6–8 sit between EFA "primary" and "secondary" rows; A-2 an in-house salaried coordinator is a lower bound. Range: low $37 (BLS median, salaried, 2025), base $65–80 (EFA primary top to secondary bottom, 2026), high $115 (EFA secondary top, 2026), USD. Medium confidence.
- **I3** from I2 + F6: cost per freelance-written 50-minute lesson. Formula: hours per lesson × hourly rate. Assumptions: A-3 hours per lesson 2–20 (no source read; F6 is corporate e-learning at 49–89 h per instruction hour and likely overstates a K-12 lesson that follows a given outline); A-4 rates from I2. Range: low 2 h × $50 ≈ $100, base 6 h × $80 ≈ $480, high 20 h × $115 ≈ $2,300 per lesson (USD, 2026). Low confidence on A-3.
- **I4** from I3 + R05 I1: program-level writing cost. Formula: 480 lessons × cost per lesson. Assumptions: A-5 480 lessons per program (R05 I1); A-6 I3 range. Range: low 480 × $100 ≈ $48,000, base 480 × $480 ≈ $230,000, high 480 × $2,300 ≈ $1,100,000 (USD), excluding staff review time. Low confidence; shows scale only.

## Gaps

- ⚠ How many hours (and what fee) does Newsela pay a freelancer per lesson, and how long does staff review of a freelance lesson take today? — why: no Tier-A source found (F2 gives no figure) — would close it: ask the partner
- ⚠ Is there a published K-12 benchmark for hours to write one lesson to a fixed outline? — why: unread: https://www.td.org/content/atd-blog/how-long-does-it-take-to-develop-one-hour-of-training-2017 (429, then a browser-verification checkpoint); unread: https://new.wvde.us/wp-content/uploads/2018/01/ExecutiveSummary_InstructionPlanningTime2013.pdf (DNS failure); cap nearly reached — would close it: read the ATD 2017 survey in a browser, or option: run anthropic-skills:deep-research for this question
- ⚠ A second independent source for freelance curriculum hourly rates (EFA is one publisher) — why: unread: https://www.upwork.com/hire/curriculum-developer/cost/ (403) — would close it: read a second rate survey
- ⚠ Answered-when evidence missing: a public benchmark of time or cost per lesson (found: cost per hour only) — would close it: the partner's own figures (first gap)

## Handoffs

- write-prd: Should NS-01 measure elapsed time (draft ready → approved, includes queue wait) or hands-on review time, or both? — rests on I1, F7
- write-prd: Should the NS-01 target wait for Newsela's own freelance baseline, or be set against the estimated range in I3 with that uncertainty stated? — rests on F2, I3, I4
- design-hld: Which lesson events (status changes, first open, edit activity, reopen) must be recorded with timestamps and actor so NS-01, SM-01 and SM-03 can be computed? — rests on I1, F7
