---
id: R05
question: "What is the usage and load profile — lessons per program, reviewers, review cadence and peak concurrent editors per lesson/unit?"
asked_in: specs/M1-lesson-generation-review/brief.md#research-questions
unblocks: "NFRs for REQ-09"
answered_when: "arithmetic from brief + any public review-process data"
status: partial
confidence: medium
supersedes: none
date: 2026-10-14
budget: 10/15 tool calls
researched_by: Claude Code, claude-opus-5-5
---

# R05 Usage and load profile for lesson review

## Answer

One full program is about 480 lessons (4 units × ~40 lessons × grades 6, 7 and 8), reviewed by a staff of 20 or more,
so each reviewer owns roughly 16–25 lessons per program; the partner states the counts but not the review cadence,
deadline or how many people edit one lesson at once. Inferred from those counts, the system carries about 20–30
concurrent users and usually 1–2 (peak about 4–5) editors on one lesson, which is tiny load for a CRDT editor;
cadence and the per-lesson peak are assumptions until the partner confirms them. Confidence: medium, because the
counts are Tier A but cadence and concurrency are inferences with no partner source. (S05.1, S05.2, S05.5)

## Takeaway

About 480 lessons and 20-plus reviewers means a small, steady team load, not web-scale traffic: the hard part is
several people safely editing the same lesson, not handling many requests.

## Findings

- **F1** [LB] A full-year program is 40 weeks split into 4 sequential units of about 40 lessons each, for each of grades 6–8 (paraphrase) — S05.1 (A), partner brief (portal) §Project brief and §Functional requirements
- **F2** [LB] Loading and editing must be performant for a review staff of 20+; generation may run asynchronously after outline upload, and a few minutes per lesson is acceptable (paraphrase) — S05.1 (A), partner brief (portal) §Performance
- **F3** [LB] The sample unit outline (G6, The Lightning Thief) has 41 numbered lesson rows, each scheduled for 1 day; types are 21 Core Reading, 9 Core Writing (2 marked double lessons), 6 Writing, 3 Spark, 2 Academic Discussion (recounted by the supervisor 2026-10-14) — S05.2 (A), sample outline CSV, columns "Lesson #", "Type of Lesson", "Days"
- **F4** The partner brief states no review cadence, approval deadline, reviewer time zones or number of reviewers per lesson — S05.1 (A), partner brief (portal), whole text read
- **F5** Google's own limit for a shared Doc is editing on up to 100 open tabs or devices at once — S05.3 (A, for Google's product; colour only for this project), Google Docs Editors Help
- **F6** Yjs describes itself as a high-performance CRDT whose shared types merge without merge conflicts, and lists a ProseMirror binding; it gives no concurrent-user figures — S05.4 (A, for Yjs's own claims), docs.yjs.dev home
- **F7** EdReports (an independent materials reviewer) organised reviewers in teams of four with one facilitator, each spending about 3–4 hours a week alone plus a weekly video meeting, over several months — S05.5 (B), Education Week 2014-11-04

## Inferences

- **I1** from F1 + F3: lessons per program. Formula: 4 units × 40 lessons × 3 grades = 480 lessons. Assumptions: A-1 every unit has about as many lessons as the sample (41); A-2 double lessons count as one record. Range: low 4 × 38 × 3 = 456, base 480, high 4 × 41 × 3 = 492 (≈ 460–500). Firm (Tier-A inputs).
- **I2** from I1 + F2: lessons per reviewer. Formula: 480 lessons ÷ reviewers. Assumptions: A-3 reviewers 20–30 ("20+"); A-4 each lesson has one owning reviewer. Range: low 480 ÷ 30 = 16, base 480 ÷ 20 = 24, high 504 ÷ 20 ≈ 25 lessons per reviewer per program. Firm on arithmetic, soft on A-4.
- **I3** from F2 + F4: peak concurrent users on the system. Formula: reviewers online at once = reviewers × share online in the busiest hour, plus 1–3 leads/designers. Assumptions: A-5 all review staff work the same business day (time zones unknown, F4); A-6 share online at peak 0.6–1.0. Range: low 20 × 0.6 + 1 = 13, base 20 × 1.0 + 2 = 22, high 30 × 1.0 + 3 = 33 concurrent users. Medium confidence.
- **I4** from F7 + I2 + F4: peak concurrent editors per lesson. Formula: owning reviewer + optional second reviewer + lead spot-check, with a review-meeting worst case of one review team on one lesson. Assumptions: A-7 normal work is one reviewer per lesson (each owns ~24 distinct lessons, I2); A-8 a review team looks like EdReports' team of four plus a facilitator (F7, one B source, 2014). Range: low 1, base 2, high 5 concurrent editors on one lesson; absolute ceiling = all staff (≈ 20–33, I3), e.g. a whole-team demo. Low-medium confidence; no partner source.
- **I5** from I3 + F6: peak edit-sync message rate. Formula: concurrent typists × updates per typist per second × burst factor. Assumptions: A-9 typists = 50–100% of I3 users; A-10 the editor sends about 1 batched update per second while typing; A-11 burst factor 3 (AI-assisted section regenerate, paste). Range: low 7 × 1 × 3 ≈ 20, base 22 × 1 × 3 ≈ 66, high 33 × 1 × 3 ≈ 100 messages per second peak across all lessons. Low confidence on A-10 (no measured source); order of magnitude is the useful part.
- **I6** from F2 + F3: generation burst when one outline lands. Formula: lessons per outline × minutes per lesson ÷ parallel workers. Assumptions: A-12 1–5 minutes per lesson ("a few minutes", F2); A-13 1–10 parallel workers. Range: low 41 × 1 ÷ 10 ≈ 4 minutes, base 41 × 3 ÷ 4 ≈ 32 minutes, high 41 × 5 ÷ 1 = 205 minutes (3.5 hours) of wall-clock per unit; 12 units (I1) per program. Medium confidence.
- **I7** from I1 + I2 + F4: review cadence needed. Formula: approvals per reviewer per day = 480 ÷ (reviewers × working days available). Assumptions: A-14 working days available D = 10–60 (no deadline given, F4). Range: low 480 ÷ (30 × 60) ≈ 0.27, base 480 ÷ (20 × 20) = 1.2, high 504 ÷ (20 × 10) ≈ 2.5 lessons approved per reviewer per day. Low confidence until the partner names a deadline.

## Gaps

- ⚠ What review cadence and deadline does Newsela plan for a 480-lesson program (lessons approved per day or per week, and by when)? — why: no Tier-A source found (F4) — would close it: ask the partner (technical contact named in the brief)
- ⚠ How many people edit one lesson at the same time in Newsela's real process (single owner, pairs, lead co-edit)? — why: no Tier-A source found; I4 rests on one 2014 B source about a different reviewer — would close it: ask the partner
- ⚠ Where are the 20+ reviewers located (time zones), which sets the peak hour and the quiet maintenance window? — why: no Tier-A source found — would close it: ask the partner, or read Newsela job posts (R03)
- ⚠ How often does the editor actually send sync updates per typing user (A-10)? — why: Yjs docs give no figure — would close it: measure in the built prototype
- ⚠ Answered-when evidence missing: public review-process data covering edit concurrency (EdReports data found covers team size and hours, not simultaneous editing) — would close it: option: run anthropic-skills:deep-research for this question

## Handoffs

- write-prd: Which numbers become the REQ-09 NFRs (base 480 lessons, ~22 concurrent users, up to 5 editors on one lesson), and which wait for partner confirmation? — rests on I1, I3, I4
- write-prd: Is a deadline-driven approval rate (I7) a success measure, or is NS-01 time-per-lesson enough? — rests on I7, F4
- design-hld: How should the system be sized for about 20–33 concurrent users, up to about 100 sync messages per second, and 1–5 simultaneous editors on one lesson? — rests on I3, I4, I5
- design-hld: How should a generation burst of 40+ lessons per outline (minutes to hours) be queued so it does not slow editing? — rests on I6, F2
