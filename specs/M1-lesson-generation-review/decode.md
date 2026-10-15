---
milestone: M1
decoded: 2026-10-14 23:26 CDT (UTC-0500)
sources: [Newsela partner brief "Lesson Content Generation and Editing/Approval Workflow" v1 (Gauntlet portal, held by the human), Newsela company panel (Gauntlet portal), sample unit outline G6 U3 (Google Sheet linked in the brief), example lesson G6 U1 L1 (Newsela CA review site linked in the brief)]
gate: G-decode
---

# Decode: Newsela Lesson Studio

## Surface ask
(paraphrase; partner material is uncleared) Newsela is entering California "Core" ELA instruction: full-year programs
of four sequential units of about forty 50-minute lessons each, for grades 6–8. Build a tool that takes a unit outline
(a spreadsheet of ~40 lessons, each naming standards, texts and a learning arc), generates each lesson with AI aligned
to the CA ELA/ELD standards it names, stores the lessons, and gives internal review staff a rich-text editing view
(with AI help) and an approval workflow that marks a lesson complete. Timebox 1–2 days.

| Req | Requirement (one line) | Source (page/section) |
|---|---|---|
| REQ-01 | Generate lessons from an uploaded/imported unit outline, aligned to the CA ELA/ELD standards each row names, using the named reference text | brief §Functional requirements, bullet 1 |
| REQ-02 | Generation knows CA Common Core ELA standards for grades 6–8 ("Program Type 1") | brief §Functional requirements, bullet 1 |
| REQ-03 | Each lesson is about 50 minutes of classroom instruction | brief §Functional requirements, bullet 1 |
| REQ-04 | Persist generated lessons in a system | brief §Functional requirements, bullet 2 |
| REQ-05 | Review and edit a lesson's content in a WYSIWYG view, with AI-assisted tooling where helpful | brief §Functional requirements, bullet 3 |
| REQ-06 | Approval workflow: once reviewed/updated a lesson is flagged complete | brief §Functional requirements, bullet 4 |
| REQ-07 | Lesson format/structure follows Newsela's example lesson | brief §Functional requirements, bullet 6 |
| REQ-08 | Generation may be asynchronous; a few minutes per lesson is acceptable | brief §Performance benchmarks |
| REQ-09 | Loading/editing performant for a staff of 20+ reviewers | brief §Performance benchmarks |
| REQ-10 | Clean, well-structured architecture | brief §Code quality |
| REQ-11 | Partner-mandated languages, AI providers and collaborative-editor toolkit (named in the brief) | brief §Technology |
| REQ-12 | Deliverables: source code, technical documentation, demo video; AI-usage doc optional | brief §Submission |
| REQ-13 | Thoughtful, easy to understand/use/navigate workflow; creativity to raise internal staff productivity | brief §"Off-limits tech" field (used as guidance) |
| REQ-14 | Timebox 1–2 days | brief §Time constraints |

## Question behind the question
| QB | Hypothesis: what this project really tests | Evidence | Confidence |
|---|---|---|---|
| QB-1 | Product judgment for an internal content-operations tool: can the builder turn a vague "generate + review + approve" ask into a workflow that measurably raises reviewer throughput, not just a generator with a text box? | Role is "Principal Product Engineer"; the only non-tech guidance is "thoughtful design and easy to understand/use/navigate workflow … improving productivity of internal staff"; company panel rates ambiguous problem solving 5/5 | high |
| QB-2 | Generation quality you can trust at program scale: lessons that match Newsela's real lesson anatomy and cite only real standards, so reviewers fix pedagogy, not structure or hallucinations | Brief links a concrete example lesson and a real outline; "aligned to teach the CA Core ELA/ELD standards numbers indicated"; a program is ~160 lessons per grade, so review time per lesson is the cost driver | high |
| QB-3 | Engineering maturity on the partner's mandated editor toolkit: real multi-reviewer collaboration plus an approval state that cannot be bypassed, built cleanly in 1–2 days | a collaborative-editor toolkit is named as a requirement; "20+ reviewers"; "clean, well structured architecture"; partner uses Claude Code/Codex, so AI-assisted speed is expected | med |

**Recommended framing for the brief:** Build the review desk Newsela's curriculum staff would actually use: an outline
goes in, structured, standards-true lessons come out in the background, and reviewers edit together and approve with
an audit trail — judged by how fast a reviewer gets a lesson from generated to approved.

## What graders / the partner will look at first
1. The demo video: outline upload → lessons generating → reviewer editing (with AI assist) → approval.
2. Whether a generated lesson looks like their own example lesson (sections, pacing summing to 50 min, standards).
3. Ease of the review workflow (navigation across ~40 lessons, status at a glance).
4. Source code structure and technical documentation.
5. Interview defense (3–4 rounds): tradeoffs, why this design, what breaks at 480 lessons and 20+ reviewers.

## Traps
| T | Trap | Why it's tempting | Cost if we fall in | Evidence | Guard (phase / skill / check) |
|---|---|---|---|---|---|
| T-1 | Literal reading: generate a free-text lesson blob per row | Fastest path; one prompt per row | Reviewers rewrite structure; output looks nothing like the example; QB-2 fails | Example lesson has a fixed anatomy (objectives, EQs, pacing table 15/30/5, sequence steps, Pulse Check, ELD supports, homework) | write-prd FRs for lesson anatomy; define-acceptance checks pacing sums to 50 and every section present |
| T-2 | Hallucinated or mis-stated standards | LLMs "know" CCSS codes loosely | Content alignment errors are exactly what adoption reviewers reject | Outline cites codes like RL.6.9.a, ELD.PI.6.6; "definitions can be found online" | R01 finds a canonical standards source; FR: every cited code resolves to a stored definition; acceptance rejects unknown codes |
| T-3 | Reproducing copyrighted anchor-text passages | Lessons reference chapters of a commercial novel | Legal exposure for the partner; looks careless | Outline anchor text is a commercial novel (ISBN given) | R07 on excerpt limits; FR: lessons reference passages by chapter/page, no long verbatim excerpts |
| T-4 | Messy outline treated as clean | The sample looks tabular | Import silently drops or misnumbers lessons | Sample has section-header rows, flex days without lesson numbers, title says U4 while filenames say U3, malformed filenames (L309, a doubled filename) | FR: import shows a preview with row-level warnings; acceptance uses the real sample outline |
| T-5 | Synchronous generation in a request | Simplest code | Timeouts at minutes per lesson × 41 lessons; demo stalls | Brief: "a few minutes per lesson is ok" | NFR for background generation with visible per-lesson progress; design-hld picks the mechanism |
| T-6 | Editor gold-plating (comments, suggestions, presence, history) | Collaborative editors invite it | Burns the 1–2 day box | REQ-11 names the stack, not features | Non-goals in write-prd; appetite cut order |
| T-7 | Approval that is just a flag anyone flips | One boolean is easy | No audit, approved lessons edited afterwards, QB-1 fails | "rigorous approval process" in business context | FRs for approval states, who/when audit, approved content locked unless reopened |
| T-8 | Unverifiable success ("it generates lessons") | Output volume is easy to count | Vanity metric; no story for the partner | Partner metric words: "ARR", "prohibitively enormous manual work" | write-prd SC tree: North Star = reviewer time from generated to approved; guard = share approved with light edits |
| T-9 | Partner-stack mismatch | Reusing a prior project's stack habits | Fails REQ-11 outright | Brief mandates the languages and editor toolkit (REQ-11) | REQ row; AGENTS.md project specifics; design-hld |
| T-10 | Deliverable gaps | Code feels like the deliverable | Missing demo video or tech docs | REQ-12 | REQ rows mapped to write-demo-script/record-demo and garden-docs; U rows for recording and portal submission |
| T-11 | Uncapped AI spend | Generating 41 rich lessons repeatedly while iterating | Real money; partner sees no cost awareness | ~41 lessons × long outputs × retries | ⚠ spend cap at GI; NFR on cost per lesson; generation of one lesson first, unit on demand |

Categories checked (each is a T row above or n/a with a reason): literal reading (T-1) · hidden grading criteria
(T-8, interview in QB list) · unstated non-functional bar (T-5, T-7, T-11) · wrong stack / partner mismatch (T-9) ·
demo vs depth (T-6) · deliverable gaps (T-10) · scope creep (T-6) · unverifiable success (T-8) · domain landmines
(T-2, T-3; no student data is involved, staff-only tool) · copying v1 / prior work (T-9).

## Open questions
- ⚠ What is your appetite and hard deadline (with timezone) for this project? Brief says 1–2 days, no submission date shown. (→ G-decode)
- ⚠ May partner material (brief, sample outline, example lesson) be quoted or committed to a public repo? Recommended: no; it stays in a gitignored folder and the repo paraphrases. (→ G-decode)
- ⚠ Which AI provider, and what spend cap for generation during development and the demo? (→ G-decode)
- ⚠ Do you want to email the technical contact with clarifying questions (e.g. what "Program Type 1" means, whether ELD supports are in scope)? (→ G-decode)

## Research questions for gather-evidence
- R01: Canonical, citable source for CA CCSS ELA/Literacy grades 6–8 and CA ELD standards, and what "Program Type 1" means in CA adoption.
- R02: Newsela CA lesson anatomy across lesson types (Spark, Core Reading, Core Writing, Academic Discussion, Writing/Showcase, Flex).
- R03: The partner: product, customers, CA Core plans, what they hire for.
- R04: The market: CA ELA adoption cycle, incumbents, ideal customer, size.
- R05: Usage and load: lessons per program, reviewer team size, review cadence and peaks.
- R06: Data that measures the North Star (reviewer time to approve; baseline cost/time of freelance lesson writing).
- R07: Limits on quoting a copyrighted anchor text inside lesson materials.
- R08: Published quality criteria for ELA instructional materials usable as a generation/review rubric.

## Interview log
| Q | Question | Recommended | Human's answer (verbatim) |
|---|---|---|---|
| — | none asked: /plan-product parks human questions for the batched GI card (WORKFLOW §4b) | — | — |

## Parking lot
- "ProseMirror and Yjs for the frontend/collaborative editor" (brief) — mandated; design-hld picks the binding.
- "prompts/agent knowledgeable on CA Core ELA Program Type 1 standards" (brief) — design-hld: retrieval of standard definitions vs prompt-stuffing.
- "Vercel or Railway … feel free" (brief) — hosting is a GD decision.
