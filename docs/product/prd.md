# Newsela Lesson Studio — Product Requirements

| Field | Value |
|---|---|
| Source brief | `specs/M1-lesson-generation-review/brief.md` @ 3785712 |
| Track | Full |
| Last updated | Wed Oct 14 23:56:00 CDT 2026 |
| Context names | Newsela |
| Approval | G1 — recorded in `.handoff/TRACKER.md ## Approvals` (never in this file) |

## Problem

Newsela is entering California's full-year ELA instruction market, which means producing about forty 50-minute
lessons for each of four units per grade, for grades 6–8, each aligned to named state standards (REQ-01, REQ-03).
Today a lesson is drafted by a freelance writer, then reviewed, revised and re-entered by staff; the partner calls
this slow, hard to coordinate and uneven in quality, and the manual effort is what has kept them out of the market
(brief, Problem; REQ-13). How much staff time a lesson costs today: not in the sources; the partner publishes no per-lesson baseline, and
public rates for freelance curriculum writing run about $50–115 an hour (R06). Why now: California's 2026 follow-up
adoption for grades TK–8 goes to a State Board vote in November 2026, and adopted content can then be revised only
about every two years, so the partner must produce and revise whole programs on the state's calendar (R04). Evidence: REQ-01–REQ-09, R02, R04,
R05, R06.

### Job stories

- **JS-01** When I have finished a unit outline of about forty lessons, I want to get a first draft of every lesson without commissioning writers, so I can spend my time judging lessons instead of waiting for them. — Source: brief JS-01 (REQ-01, REQ-08)
- **JS-02** When a drafted lesson lands in my list, I want to see at once which standards, texts and minutes it covers and whether it matches our lesson anatomy, so I can catch structural or alignment problems in seconds. — Source: brief JS-02 (REQ-02, REQ-03, REQ-07)
- **JS-03** When a lesson is mostly right but a section is weak, I want to rewrite or regenerate just that part with help, in place, so I can fix it without redoing the whole lesson. — Source: brief JS-03 (REQ-05)
- **JS-04** When several of us are working through the same unit, I want to edit alongside colleagues without overwriting each other, so I can keep twenty reviewers moving in parallel. — Source: brief JS-04 (REQ-09, REQ-11)
- **JS-05** When I am satisfied with a lesson, I want to mark it complete with a record of who signed off and when, so I can trust that approved lessons stay approved and the unit's progress is visible. — Source: brief JS-05 (REQ-06)
- **JS-06** When I check on a unit, I want to see how many lessons are drafted, in review and approved, so I can know whether the program will be ready on time. — Source: brief JS-06 (REQ-06, REQ-13)

## Users and personas

| Persona | Who they are | Context of use | What they need | How often |
|---|---|---|---|---|
| Rosa, reviewer (primary) | Newsela curriculum review staff member, one of 20+ | works through a unit's drafted lessons, editing and signing off | a lesson that already has the right shape and standards, help fixing weak parts, a clear approve step | daily during a program build |
| Dev, instructional designer | writes the unit outline (≈40 lessons, learning arc, standards, texts) | after finishing an outline | to turn the outline into drafts without commissioning writers | once per unit (4 per grade) |
| Lena, content lead | owns a grade's program schedule | checks progress across units | counts by status, who is stuck | several times a week |

Not for: teachers and students — this is an internal production tool; the published lesson experience already
exists (R02). Not for: freelance writers — the product replaces the drafting step they did.

## Goals

- **GOAL-1** A reviewer gets a lesson from "draft ready" to "approved" in far less working time than the freelance-draft flow. Measured by: SC-001, SC-002.
- **GOAL-2** Drafts arrive already shaped like the partner's house lesson and aligned to real standards, so review is about pedagogy, not structure. Measured by: SC-003.
- **GOAL-3** Approval stays trustworthy: approved lessons are rarely reopened for content problems. Measured by: SC-004.

## Non-goals and no-gos

Non-goals:
- **NG-1** Publishing approved lessons into the partner's live lesson experience — because the brief stops at "flagged as complete"; revisit after the demo with the partner.
- **NG-2** A student-facing lesson view — because reviewers work on the teacher edition (R02); revisit never in this appetite.
- **NG-3** Generating assessments, flex-day plans or research lessons — because the sample outline gives no lesson number or standards for flex rows; revisit when an outline describes them.
- **NG-4** Comments, suggestion mode and version-diff views in the editor — because the 1–2 day appetite cannot hold them (decode T-6); revisit after M5.
- **NG-5** Authoring or editing the outline inside the product — because outlines are written in spreadsheets today (REQ-01); revisit never.
- **NG-6** Multiple programs, grades and states at once — because one unit proves the workflow; data for more units is allowed but not designed for in screens.

No-gos:
- **NOGO-1** Reproducing long passages of a copyrighted anchor text inside a lesson — because published lessons cite short page-referenced excerpts (R02 I3, R07).
- **NOGO-2** Citing a standard code the system cannot resolve to its official text — because misaligned standards are what adoption reviewers reject (decode T-2).
- **NOGO-3** Any student or personal data — none is needed for an internal content tool.

## Appetite

- Time box: 1–2 days of build after design (REQ-14); hard date: none set on the portal; two days of build from the start of M4, US Central time. Source: REQ-14, D11.
- If time runs short, cut in this order: US-7 → US-6 → US-5 → US-4. Never cut: US-1, US-2, US-3 and the [Unwanted] FRs of those stories.

## User stories

### US-1 Turn an outline into drafted lessons (P1)

As Dev, the instructional designer, I want to upload a unit outline and get every lesson drafted in the background, so that reviewers have drafts without commissioning writers.

- Why this priority: without drafts there is nothing to review; this is the market-entry bottleneck.
- Independent test: upload the sample G6 outline, confirm the preview, and watch lessons move from Queued to Draft ready; open one and see all sections.
- Requirements: FR-001, FR-002, FR-003, FR-004, FR-005, FR-006, FR-007, FR-008, FR-009, FR-010, FR-032, FR-033, FR-034 · Examples: AE-001–AE-010, AE-030, AE-033, AE-034, AE-035

### US-2 Review and edit a drafted lesson (P1)

As Rosa, a reviewer, I want to open a drafted lesson in a formatted editor with its standards beside it, so that I can fix it in place.

- Why this priority: reviewers spend their day here; the brief asks for WYSIWYG editing.
- Independent test: open a seeded draft, change a sentence, reload, see the change kept and the status "In review".
- Requirements: FR-011, FR-012, FR-013 · Examples: AE-011, AE-012, AE-013

### US-3 Approve a lesson with a record (P1)

As Rosa, I want to approve a lesson once it is right, with my name and the time recorded and the lesson locked, so that approved content stays approved.

- Why this priority: approval is the brief's definition of done for a lesson.
- Independent test: approve a passing lesson, see it locked and the history row; try to approve a failing one and see it blocked.
- Requirements: FR-014, FR-015, FR-016, FR-017, FR-018, FR-031 · Examples: AE-014–AE-018, AE-029

### US-4 Fix part of a lesson with AI help (P2)

As Rosa, I want to select a passage or a segment and ask for a rewrite with my instruction, then accept or reject it, so that I fix weak parts without retyping them.

- Why this priority: the brief asks for AI-assisted tooling; it shortens review time (SC-001).
- Independent test: select a Launch segment, ask "make the question easier for emerging English learners", accept, see the text replaced.
- Requirements: FR-019, FR-020, FR-021, FR-022, FR-023 · Examples: AE-019–AE-023

### US-5 Edit together in real time (P2)

As Rosa, I want to see colleagues' edits and presence live in the same lesson, so that two of us can work one lesson without overwriting each other.

- Why this priority: the partner mandates a collaborative editor and 20+ reviewers (REQ-09, REQ-11).
- Independent test: open one lesson in two browsers as two reviewers, type in both, see both edits in both within a second.
- Requirements: FR-024, FR-025, FR-026 · Examples: AE-024, AE-025, AE-026

### US-6 See unit progress at a glance (P2)

As Lena, the content lead, I want a unit page with counts by status and each lesson's status, so that I know if the program is on schedule.

- Why this priority: progress visibility is the lead's job story (JS-06) and the demo's opening shot.
- Independent test: with seeded lessons in mixed statuses, the unit page shows the right counts and filters by status.
- Requirements: FR-027, FR-028 · Examples: AE-027, AE-028

### US-7 Approve against a quality checklist (P3)

As Rosa, I want a short quality checklist at approval time, so that every reviewer applies the same bar.

- Why this priority: guards SC-004, but approval works without it.
- Independent test: approve a lesson, see the checklist, leave one item unticked and see approval wait.
- Requirements: FR-029, FR-030 · Examples: AE-031, AE-032

## Functional requirements

- **FR-001** [Event] (US-1) When an instructional designer uploads a unit outline spreadsheet, the system shall show a preview listing every lesson row found with its lesson number, title, lesson type and focus standards.
- **FR-002** [Unwanted] (US-1) If an outline row has no lesson number, repeats a lesson number or has no focus standards, then the system shall show that row in the preview with a warning naming the problem.
- **FR-003** [Event] (US-1) When the designer confirms the preview, the system shall create one lesson per numbered lesson row, in outline order, with status "Queued".
- **FR-004** [Event] (US-1) When lessons are queued, the system shall draft them in the background and show each lesson's status as Queued, Generating, Draft ready or Failed on the unit page.
- **FR-005** [Ubiquitous] (US-1) The system shall produce every draft with the partner's lesson sections: header with type, title, minutes and standards; learning objectives; essential questions; connections; pacing plan; lesson sequence segments; homework; and lesson texts.
- **FR-006** [Unwanted] (US-1) If a draft's segment minutes do not add up to the lesson's stated minutes, then the system shall mark the draft as failing the pacing check.
- **FR-007** [Unwanted] (US-1) If a draft cites a standard code that is not in the stored California standards list, then the system shall mark that code as unknown on the lesson.
- **FR-008** [Ubiquitous] (US-1) The system shall show the official text of every standard code shown on a lesson.
- **FR-034** [Event] (US-1) When the evaluation run is started, the system shall report for each sampled lesson type how its draft compares with a published partner lesson of the same type on section coverage, pacing and standards coverage.
- **FR-033** [Event] (US-1) When an outline or draft writes a standard code in a different spelling of an official code (for example W.6.2.c for W.6.2c), the system shall show the official spelling beside the code as written.
- **FR-009** [Unwanted] (US-1) If drafting one lesson fails, then the system shall mark only that lesson Failed and offer a retry.
- **FR-010** [Unwanted] (US-1) If a draft contains a quoted passage longer than 50 words, then the system shall flag that passage for the reviewer.
- **FR-011** [Event] (US-2) When a reviewer opens a lesson, the system shall show its content formatted, with headings and lists, beside a panel listing its standards and check results.
- **FR-012** [Event] (US-2) When a reviewer changes lesson content, the system shall keep the change without a save action.
- **FR-013** [Complex] (US-2) While a lesson is Draft ready, when a reviewer first changes it, the system shall change its status to In review.
- **FR-014** [Event] (US-3) When a reviewer approves a lesson, the system shall set its status to Approved with the approver's name and the time.
- **FR-015** [Unwanted] (US-3) If a lesson has a failing pacing check or an unknown standard code, then the system shall refuse approval and list the failing checks.
- **FR-016** [State] (US-3) While a lesson is Approved, the system shall show its content read-only.
- **FR-017** [Event] (US-3) When a reviewer reopens an Approved lesson with a reason, the system shall set its status to In review and record who, when and why.
- **FR-018** [Ubiquitous] (US-3) The system shall show each lesson's history of status changes with person and time.
- **FR-019** [Event] (US-4) When a reviewer selects lesson text and submits an instruction to the assistant, the system shall show a proposed replacement next to the original.
- **FR-020** [Event] (US-4) When the reviewer accepts a proposal, the system shall replace the selected text with the proposal.
- **FR-021** [Event] (US-4) When the reviewer rejects a proposal, the system shall leave the lesson text unchanged.
- **FR-022** [Event] (US-4) When a reviewer asks to regenerate one lesson segment, the system shall show a new version of only that segment as a proposal.
- **FR-023** [Unwanted] (US-4) If the assistant cannot produce a proposal, then the system shall tell the reviewer and leave the lesson unchanged.
- **FR-024** [State] (US-5) While two or more reviewers have the same lesson open, the system shall show each reviewer's edits and presence to the others.
- **FR-025** [Unwanted] (US-5) If two reviewers edit the same paragraph at the same moment, then the system shall keep both reviewers' edits.
- **FR-026** [Unwanted] (US-5) If a reviewer loses connection while editing, then the system shall merge that reviewer's offline edits when the connection returns.
- **FR-027** [Ubiquitous] (US-6) The system shall show, on the unit page, the number of lessons in each status and each lesson's status and last editor.
- **FR-028** [Event] (US-6) When a lead picks a status filter on the unit page, the system shall list only lessons in that status.
- **FR-029** [Event] (US-7) When a reviewer starts approving a lesson, the system shall show the quality checklist for that lesson type.
- **FR-030** [Unwanted] (US-7) If any checklist item is unticked, then the system shall keep the lesson unapproved.
- **FR-031** [Unwanted] (US-3) If a person who is not signed in as staff opens any lesson or unit, then the system shall show the sign-in page instead.
- **FR-032** [Unwanted] (US-1) If the designer uploads an outline for a unit that already has lessons, then the system shall ask whether to add only new lesson numbers before changing anything.

## Non-functional requirements

- **NFR-001** [Performance] One lesson is drafted within 5 minutes at the 95th percentile after it starts generating. Source: REQ-08.
- **NFR-002** [Capacity] A 41-lesson unit is fully drafted within 60 minutes of confirming the outline. Source: D12.
- **NFR-003** [Performance] A lesson opens ready to edit in ≤ 2 s at the 95th percentile with 25 reviewers active. Source: REQ-09 (20+ reviewers) and R05.
- **NFR-004** [Performance] An edit appears in a colleague's open copy of the lesson within 1 s at the 95th percentile with 5 reviewers in one lesson. Source: REQ-09, R05.
- **NFR-005** [Reliability] 100 % of accepted edits survive a reload, a dropped connection or a restart. Source: REQ-04.
- **NFR-006** [Auditability] 100 % of lesson status changes are traceable to a person and time. Source: REQ-06.
- **NFR-007** [Cost] AI spend per drafted lesson is ≤ $0.50 at list prices. Source: D6 ($30 total during the build).
- **NFR-008** [Accessibility] The unit page, lesson editor and approval steps meet WCAG 2.2 AA. Source: REQ-13 (usable, navigable workflow); assumed level, see A-5.
- **NFR-009** [Capacity] One program of 480 lessons (4 units × 40 lessons × 3 grades) with 25 users is handled without changing the above numbers. Source: REQ-09, R05.

## Success criteria

- **SC-001** North Star: median reviewer working time per lesson from "Draft ready" to "Approved". Target ≤ 60 minutes (aspirational), grounded in a reviewer reading one 50-minute lesson end to end plus fixes, because no public per-lesson baseline exists (R06) — the first demo unit sets the real baseline; lagging; if bad we fix the drafting of the sections reviewers rewrite most, or the editing aids; measured by status-change times and active editing time per lesson; reviewed by the content lead every week of a program build. (GOAL-1)
- **SC-002** Supporting (explains SC-001): share of lessons approved with light edits (under 20 % of the draft's words changed). Target ≥ 60 % (aspirational), grounded in the brief's aim to "supplant the manual lesson writing step" (REQ-01) — if most drafts need heavy rewriting, drafting has not replaced writing; leading; if bad we fix drafting for the lesson types with the heaviest edits; measured by comparing each approved lesson with its first draft. (GOAL-1)
- **SC-003** Supporting (explains SC-001): share of drafts that pass the structure, pacing and standards checks on the first attempt. Target ≥ 90 % (hard gate for the demo unit), grounded in decode T-1 and T-2 — a failing draft costs a reviewer a regeneration before any review; leading; if bad we fix the drafting instructions for the failing check; measured by check results at drafting time and by the evaluation run against published partner lessons (FR-034, decode QB-4/T-12). (GOAL-2)
- **SC-004** Supporting (guards SC-001): share of approved lessons reopened for a content problem. Target ≤ 5 % (hard gate), grounded in the brief's "rigorous approval process" — approvals rushed to look good would reopen later, which means SC-001 was gamed; lagging; if bad we tighten the approval checklist (US-7); measured by reopen events per approved lesson. (GOAL-3)

Rejected as vanity: lessons generated (counts output, not usable lessons); tokens used (cost context only, kept in NFR-007); editor sessions opened (activity, not progress).

## Acceptance examples

- **AE-001** (FR-001) Given Dev has the sample grade 6 unit outline with 41 numbered lessons, When Dev uploads it, Then the preview lists 41 lessons from "Lesson 1 What Are Myths?" to "Lesson 41", each with type and focus standards.
- **AE-002** (FR-002) Given an outline whose row for Lesson 12 has no focus standards and whose rows repeat "Lesson 30", When Dev uploads it, Then the preview shows a warning on Lesson 12 ("no focus standards") and on both Lesson 30 rows ("duplicate lesson number").
- **AE-003** (FR-003) Given the preview of the sample outline with 4 flex-day rows that have no lesson number, When Dev confirms, Then the unit holds exactly 41 lessons in outline order, all "Queued", and no flex-day lesson.
- **AE-004** (FR-004) Given 41 lessons are Queued, When Dev closes the browser and returns 10 minutes later, Then the unit page shows some lessons "Draft ready" and the rest "Generating" or "Queued".
- **AE-005** (FR-005) Given "Lesson 4 Chapter 1" (Core Reading, focus RL.6.1, RL.6.2, L.6.4) is Draft ready, When Rosa opens it, Then it shows a header, three learning objectives, an essential question, connections, a pacing plan, numbered segments ending with Homework, and the anchor text under lesson texts.
- **AE-006** (FR-006) Given a draft whose pacing plan lists Launch 5, Literacy Lab 10, Learning in Action 30, Look Back 10 for a 50-minute lesson, When the checks run, Then the lesson shows "Pacing check failed: 55 of 50 minutes".
- **AE-007** (FR-007) Given a draft citing RL.6.99, When the checks run, Then the standards panel shows "RL.6.99 — unknown code" in red.
- **AE-008** (FR-008, FR-011) Given Lesson 1 cites RI.6.1, When Rosa opens it, Then the standards panel shows RI.6.1 with its official text.
- **AE-009** (FR-009) Given drafting of Lesson 9 times out while Lessons 8 and 10 succeed, When Dev views the unit, Then Lesson 9 is "Failed" with a Retry action and Lessons 8 and 10 are "Draft ready".
- **AE-010** (FR-010) Given a draft that quotes a 75-word passage from the anchor novel, When Rosa opens it, Then that passage is highlighted with "Long quotation — check permissions".
- **AE-011** (FR-012) Given Rosa changes "Turn and Talk" to "Think-Pair-Share" in Lesson 2, When she reloads the page, Then the lesson shows "Think-Pair-Share".
- **AE-012** (FR-013) Given Lesson 2 is Draft ready, When Rosa types one character into it, Then its status becomes "In review".
- **AE-013** (FR-011) Given Lesson 5 is Draft ready, When Rosa opens it, Then headings and bulleted lists display formatted, not as raw markup, and the standards panel is beside the text.
- **AE-014** (FR-014, FR-018) Given Lesson 3 is In review with all checks passing, When Rosa approves it at 10:42, Then its status is Approved and its history shows "Approved by Rosa at 10:42".
- **AE-015** (FR-015) Given Lesson 6 has a failing pacing check, When Rosa tries to approve it, Then approval is refused and the message lists "Pacing check failed".
- **AE-016** (FR-016) Given Lesson 3 is Approved, When Rosa opens it, Then the text cannot be changed and the page says "Approved — reopen to edit".
- **AE-017** (FR-017, FR-018) Given Lesson 3 is Approved, When Lena reopens it with reason "wrong chapter cited", Then it is In review and the history shows Lena, the time and the reason.
- **AE-018** (FR-018) Given Lesson 7 went Queued → Draft ready → In review → Approved, When Lena opens its history, Then four entries show, each with person (or "system") and time.
- **AE-019** (FR-019) Given Rosa selects the Launch question in Lesson 2, When she asks "simplify for emerging English learners", Then a proposed rewrite appears beside the original.
- **AE-020** (FR-020) Given a proposal for the Launch question is shown, When Rosa accepts it, Then the Launch question reads as the proposal.
- **AE-021** (FR-021) Given a proposal for the Launch question is shown, When Rosa rejects it, Then the Launch question is unchanged.
- **AE-022** (FR-022) Given Lesson 8's Look Back segment is weak, When Rosa asks to regenerate that segment, Then a new Look Back proposal appears and every other segment is unchanged.
- **AE-023** (FR-023) Given the assistant service is unreachable, When Rosa submits an instruction, Then she sees "The assistant could not answer; your lesson is unchanged" and the text is unchanged.
- **AE-024** (FR-024) Given Rosa and Sam both have Lesson 10 open, When Sam types a sentence, Then Rosa sees the sentence and Sam's name marker within a second.
- **AE-025** (FR-025) Given Rosa and Sam type in the same paragraph of Lesson 10 at the same moment, When both stop, Then the paragraph contains both reviewers' words.
- **AE-026** (FR-026) Given Rosa loses her connection and types two sentences, When the connection returns, Then both sentences appear for Sam.
- **AE-027** (FR-027) Given the unit has 30 Draft ready, 8 In review and 3 Approved lessons, When Lena opens the unit page, Then it shows those three counts and each lesson's status and last editor.
- **AE-028** (FR-028) Given the same unit, When Lena filters by "In review", Then exactly 8 lessons are listed.
- **AE-029** (FR-031) Given a visitor who is not signed in, When they open a lesson link, Then the sign-in page shows and no lesson text is visible.
- **AE-033** (FR-033) Given the sample outline's Lesson 11 lists W.6.2.c, When Dev views the preview, Then the code shows with "official: W.6.2c" beside it.
- **AE-034** (FR-007) Given the sample outline's Lesson 22 lists RL.6.9.a, which has no official substandard, When its draft is checked, Then RL.6.9.a is marked unknown.
- **AE-035** (FR-034) Given three published partner lessons (one Spark, one Reading, one Writing) held out as references, When the evaluation run is started, Then a report lists each type with its section coverage, pacing result and standards coverage, and the overall pass share.
- **AE-030** (FR-032) Given the unit already has 41 lessons, When Dev uploads the same outline again, Then the system asks "Add only new lesson numbers?" and nothing changes until Dev answers.
- **AE-031** (FR-029) Given Lesson 4 is a Core Reading lesson, When Rosa clicks Approve, Then a checklist for reading lessons appears.
- **AE-032** (FR-030) Given the checklist with one item unticked, When Rosa confirms approval, Then Lesson 4 stays In review and the unticked item is highlighted.

## Edge cases

- **EC-1** Empty outline or a file with no recognisable lesson rows → expected: preview shows "No lessons found" and nothing is created (FR-002)
- **EC-2** Outline title and lesson file names disagree on the unit number (sample says U4 and U3) → expected: preview shows the outline title and a warning (FR-002)
- **EC-3** Flex-day and section-header rows without lesson numbers → expected: listed in the preview as skipped, not drafted (FR-003)
- **EC-4** Re-uploading an outline for a unit that has lessons → expected: asks before adding (FR-032)
- **EC-5** Two reviewers approve the same lesson within a second → expected: one approval recorded, the second sees it is already Approved (FR-014)
- **EC-6** A reviewer edits while another approves → expected: the approval locks the lesson; edits arriving after approval are refused with a message (FR-016)
- **EC-7** The AI provider is down for the whole unit → expected: lessons go Failed with retry; nothing else breaks (FR-009)
- **EC-8** A draft cites a standard the outline did not list → expected: shown on the lesson; the reviewer decides (FR-008)

## Assumptions and open questions

Assumptions:
- **A-1** Generation covers only numbered lessons; flex days, assessments and research lessons are not drafted (NG-3). — Basis: confirmed by the human at GI (D8 for A-2, D10 for A-1 and A-3).
- **A-2** Any signed-in reviewer may approve; there is no separate approver role. — Basis: confirmed by the human at GI (D8 for A-2, D10 for A-1 and A-3).
- **A-3** Drafts include Integrated ELD supports and Additional Student Support, because the outline names designated ELD standards per lesson and every published lesson has them (R02 F5, F6), even though Program Type 1 requires alignment to the ELA standards only (R01). — Basis: confirmed by the human at GI (D8 for A-2, D10 for A-1 and A-3).
- **A-4** Reviewers own their copy of the anchor text; lessons reference it by chapter and page (R02 I3, R07). — Basis: confirmed by the human at GI (D8 for A-2, D10 for A-1 and A-3).
- **A-5** WCAG 2.2 AA is the accessibility bar for staff screens. — Basis: confirmed by the human at GI (D8 for A-2, D10 for A-1 and A-3).
- **A-6** Staff sign-in for the demo uses seeded fictional staff accounts; connecting the partner's real staff sign-in is out of scope. — Basis: confirmed by the human at GI (D8 for A-2, D10 for A-1 and A-3).

Open questions:
- None open. Lesson types to draft: every numbered type in the outline (Spark, Core Reading, Core Writing, Academic Discussion, Showcase Writing), per D10.

### Interview log

Answered from sources: Problem → REQ-01, REQ-13, R04, R06 · Users → REQ-09, R02 · Appetite → REQ-14 · lesson anatomy → R02 · standards → R01 · usage → R05 · copyright → R07 · quality bar → R08

| Q# | Question | Recommended (and evidence) | Reply (verbatim) | Landed in |
|---|---|---|---|---|
| — | none asked in this session: /plan-product batches human questions into the GI card (WORKFLOW §4b) | — | — | open questions, A-1–A-6 |

## Risks

| Id | Risk | Type | Likelihood | Impact | Mitigation in this PRD |
|---|---|---|---|---|---|
| RISK-1 | Drafts read as generic and reviewers rewrite most of them | value | M | H | FR-005 structure, SC-002 light-edit share, US-4 targeted fixes |
| RISK-2 | Standards misaligned or invented | viability | M | H | FR-007, FR-008, FR-015, NOGO-2 |
| RISK-3 | Collaborative editing plus AI assist does not fit 1–2 days | feasibility | H | M | cut order US-7 → US-6 → US-5 → US-4 |
| RISK-4 | Long anchor-text quotations create a permissions problem for the partner | viability | L | H | FR-010, NOGO-1 |
| RISK-5 | AI spend runs over during iteration | viability | M | M | NFR-007 and its open spend question |

## Milestone cut

| Milestone | Goal (one line) | Scope (FR ids) | Proves (SC / AE ids) | Exit demo (one sentence) |
|---|---|---|---|---|
| M1 Research | Approved brief + cited research | none (docs only) | GI approval | Reviewer reads the brief and every R note |
| M2 Product | Approved PRD (+ clarifications) | none (docs only) | GI approval | Reviewer reads docs/product/prd.md |
| M3 Design | Approved HLD, LLD, data design, contract, diagrams | none (docs only) | GD approval | Reviewer can read every design doc from docs/README.md |
| M4 Tracer bullet | Outline in → drafted lessons → edit → approve | FR-001, FR-002, FR-003, FR-004, FR-005, FR-006, FR-007, FR-008, FR-033, FR-034, FR-009, FR-011, FR-012, FR-013, FR-014, FR-015, FR-016, FR-017, FR-018, FR-031 | AE-001–AE-009, AE-011–AE-018, AE-029, AE-033, AE-034, AE-035, SC-003 | Dev uploads the sample outline, Rosa edits Lesson 4 and approves it, and the unit page shows it Approved |
| M5 Review power | AI assist, live co-editing, unit progress | FR-010, FR-019, FR-020, FR-021, FR-022, FR-023, FR-024, FR-025, FR-026, FR-027, FR-028, FR-032 | AE-010, AE-019–AE-028, AE-030, SC-001, SC-002 | Two reviewers co-edit Lesson 10, one rewrites a segment with the assistant, and Lena sees counts change |
| Later | Not in this appetite | FR-029, FR-030 | AE-031, AE-032, SC-004 | — |

## Constraints

| Id | Constraint | Names | Mandated by | Source |
|---|---|---|---|---|
| C-1 | Build in JavaScript/TypeScript with Next.js on Node and React; Python allowed if desired | JavaScript, TypeScript, Next.js, Node, React, Python | partner | REQ-11 (partner brief §Technology) |
| C-2 | The collaborative lesson editor uses ProseMirror and Yjs | ProseMirror, Yjs | partner | REQ-11 (partner brief §Technology, Other requirements) |
| C-3 | AI generation and assistance use the OpenAI or Anthropic APIs | OpenAI, Anthropic | partner | REQ-11 (partner brief §Technology) |
| C-4 | Hosting on any platform; the partner uses AWS and names Vercel or Railway as fine | AWS, Vercel, Railway | partner (choice left open) | REQ-11 (partner brief §Technology) |
| C-5 | Deliver source code, technical documentation and a demo video; AI-usage documentation optional | none | partner | REQ-12, REQ-15 |
| C-6 | Build time 1–2 days; two days chosen, US Central | none | partner, human | REQ-14, D11 |
| C-7 | AI provider is Anthropic; total AI spend during the build ≤ $30 | Anthropic | human | D6 |
| C-8 | Partner material is paraphrased in the repo, never committed verbatim | none | human | D7 |

### Assignment trace

| REQ | What it asks (short) | Covered by |
|---|---|---|
| REQ-01 | Generate lessons from an uploaded outline | FR-001, FR-003, FR-004, US-1 |
| REQ-02 | Knows CA ELA grades 6–8 standards | FR-007, FR-008, FR-033, NOGO-2 |
| REQ-03 | ~50-minute lessons aligned to named standards and text | FR-005, FR-006 |
| REQ-04 | Persist lessons | FR-012, NFR-005 |
| REQ-05 | WYSIWYG review/edit with AI help | FR-011, FR-019–FR-023 |
| REQ-06 | Approval flags a lesson complete | FR-014–FR-018 |
| REQ-07 | Newsela lesson format | FR-005, R02 |
| REQ-08 | Async generation, minutes per lesson fine | FR-004, NFR-001 |
| REQ-09 | Performant for 20+ reviewers | NFR-003, NFR-004, NFR-009 |
| REQ-11 | Mandated languages, editor, AI providers | C-1, C-2, C-3, C-4, C-7 |
| REQ-12 | Code, docs, demo video | C-5 |
| REQ-13 | Easy workflow, staff productivity | SC-001, US-6, NFR-008 |
| REQ-14 | 1–2 days | C-6, Appetite |
| REQ-15 | AI usage doc optional | C-5 |

## Change log

| Date | Change | Ids affected | Gate |
|---|---|---|---|
| Wed Oct 14 23:40 CDT 2026 | First draft | all | G1 (folded into GI) |
| Wed Oct 14 23:56:00 CDT 2026 | GI answers applied: open questions closed (D6, D10–D12); A-1–A-6 confirmed; FR-034 + AE-035 evaluation against published partner lessons (decode QB-4/T-12, D14) | FR-034, AE-035, NFR-002, NFR-007, SC-003, C-6–C-8, A-1–A-6 | GI |

## Clarifications

None yet.
