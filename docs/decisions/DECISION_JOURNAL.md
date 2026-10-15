# Decision journal

Why each design choice was made and what it cost (software-factory-kit WORKFLOW.md §9). Committed, append-only.

- Written only by the `log-decision` skill, after every gate. It records decisions the **human** made; an entry is
  never `accepted` without the human's quoted words.
- Never renumber or delete an entry. Change your mind by adding a new D-row and marking the old one
  `superseded-by D<m>`. Rejected options stay visible.
- One-way (Type 1) decisions are also promoted to `docs/decisions/NNNN-<slug>.md`.
- Who said yes, word for word, lives in `.handoff/TRACKER.md ## Approvals`; this file holds the reasoning.
- Topics group decisions in the project review, `docs/decisions/REVIEW.md`, which
  `scripts/decision-views.sh` generates from this ledger. Changing the list is itself a decision.

Topics: Product · Data · Security · Money · Infrastructure · Process

## Entry schema

Copy this block for each new entry (D-ids increase by one, starting at D1):

```markdown
### D<n> <title>  [status: proposed | accepted | superseded-by D<m> | rejected]
- Date (`date`) · phase · milestone · Decided by: human · Proposed by: <skill> (<harness>, <model>) · artifact@<sha>
- Context and forces (FR/NFR ids)
- Options: always includes "do nothing" and the agent's first proposal ("instead of")
- Choice · Why (Y-statement: in context C, facing F, we chose X over Y to get Z, accepting W)
- Cost accepted · Reversibility (Type 1 one-way / Type 2 two-way) · Confidence (low/med/high)
- Revisit if · Evidence (file:line, R/S ids) · Interview line (one sentence you'd say out loud)
- Review: Topic <topic> · Weight <●●●|●●○|●○○> · One-liner: <at most 15 words>
```

## Entries

<!-- log-decision appends D1 below this line. -->

### D1 Partner material stays in a gitignored folder  [status: accepted (auto, Type 2)]
- 2026-10-14 23:38 CDT · phase 1 sharpen-brief · M1 · Decided by: supervisor under the standing rule (Type 2 proceeds, WORKFLOW §5) · Proposed by: plan-product (claude-code, claude-opus-5-5) · brief.md@3785712
- Context and forces: the partner brief, sample outline and example lessons are uncleared (U-01); the repo may become public.
- Options: Do nothing (commit the scrape) — rejected: one-way leak if the repo goes public · Gitignored `docs/source/raw/`, repo paraphrases (agent's recommendation; agent's first proposal — no instead-of recorded) — chosen · Keep outside the repo — rejected: agents lose easy access
- Choice · Why: in context of uncleared partner material, facing a possibly public repo, we chose a gitignored folder over committing it to keep the option of publishing open, accepting that a fresh clone lacks the sources.
- Cost accepted: a new clone must re-scrape. · Reversibility: Type 2 · Confidence: high
- Revisit if: the human answers U-01 "may commit". · Evidence: brief U-01, decode ⚠ · Interview line: "Partner material stays local until they say it can be public."
- Review: Topic Process · Weight ●○○ · One-liner: Partner docs kept local and gitignored until cleared.

### D2 make check skips npm steps until the app exists  [status: accepted (auto, Type 2)]
- 2026-10-14 23:38 CDT · phase 0 init · M1 · Decided by: supervisor under the standing rule (Type 2 proceeds, WORKFLOW §5) · Proposed by: plan-product (claude-code, claude-opus-5-5) · Makefile@0b02cc8
- Context and forces: the human asked to make `make check` real; there is no code during planning milestones.
- Options: Do nothing (template fails on purpose) — rejected: planning commits could never pass the pre-push hook · Guard on package.json, run npm lint/typecheck/test once it exists (agent's recommendation; agent's first proposal — no instead-of recorded) — chosen · Scaffold the app now — rejected: picks the stack before GD
- Choice · Why: in context of a docs-only milestone, facing a hook that runs make check, we chose a package.json guard over scaffolding now to keep stack choices at GD, accepting that check is docs-only until M4.
- Cost accepted: checks are thin until the first build milestone. · Reversibility: Type 2 · Confidence: high
- Revisit if: package.json lands without lint/typecheck/test scripts. · Evidence: Makefile:16-26 · Interview line: "The gate is real from day one and grows with the code."
- Review: Topic Process · Weight ●○○ · One-liner: make check guards npm steps on package.json.

### D3 Research fanned out to parallel agents with source fragments  [status: accepted (auto, Type 2)]
- 2026-10-14 23:38 CDT · phase 2 gather-evidence · M1 · Decided by: supervisor under the standing rule (Type 2 proceeds, WORKFLOW §5) · Proposed by: plan-product (claude-code, claude-opus-5-5) · docs/research@639bdbe
- Context and forces: eight research questions; gather-evidence says parallel runs conflict on sources.md.
- Options: Do nothing (serial, one session) — rejected: ~4x slower · Three parallel agents each writing a sources fragment, merged by the supervisor (agent's recommendation; agent's first proposal — no instead-of recorded) — chosen
- Choice · Why: in context of independent questions, facing the shared sources.md, we chose per-agent fragments merged once over serial runs to cut wall-clock, accepting one manual merge (it caught one URL with two S-ids, fixed).
- Cost accepted: a merge step; a supervisor recount fixed one agent miscount (R05 F3). · Reversibility: Type 2 · Confidence: high
- Revisit if: merges keep finding conflicts. · Evidence: docs/research/sources.md · Interview line: "Parallel research, single merge, so the log stays one truth."
- Review: Topic Process · Weight ●○○ · One-liner: Parallel research agents, fragments merged into one sources log.

### D4 Milestone cut: tracer bullet then review power  [status: accepted (auto, Type 2)]
- 2026-10-14 23:38 CDT · phase 3 write-prd · M2 · Decided by: supervisor under the standing rule (Type 2 proceeds, WORKFLOW §5) · Proposed by: plan-product (claude-code, claude-opus-5-5) · docs/product/prd.md@7f56978
- Context and forces: 1–2 day appetite (REQ-14); P1 = outline→draft→edit→approve (US-1–US-3).
- Options: Do nothing (one big build milestone) — rejected: no early try-it point · M4 tracer (US-1–3) then M5 (US-4–6), US-7 later (agent's recommendation; agent's first proposal — no instead-of recorded) — chosen · Collaboration first — rejected: nothing to review without drafts
- Choice · Why: in context of a short appetite, facing three P1 stories, we chose a tracer bullet then review power to get a try-it link early, accepting that co-editing (a partner mandate) lands in M5.
- Cost accepted: the mandated collaborative editor is only fully shown in M5. · Reversibility: Type 2 · Confidence: med
- Revisit if: the human wants co-editing in the tracer. · Evidence: prd.md ## Milestone cut · Interview line: "Prove the whole path thin first, then make review fast."
- Review: Topic Product · Weight ●●○ · One-liner: M4 tracer bullet, M5 AI assist and co-editing.

### D5 North Star target 60 minutes per lesson, aspirational  [status: accepted (auto, Type 2)]
- 2026-10-14 23:38 CDT · phase 3 write-prd · M2 · Decided by: supervisor under the standing rule (Type 2 proceeds, WORKFLOW §5) · Proposed by: plan-product (claude-code, claude-opus-5-5) · docs/product/prd.md@7f56978
- Context and forces: no public per-lesson baseline (R06); a lesson is 50 minutes of instruction.
- Options: Do nothing (no target) — rejected: METRICS §4 wants a grounded target or a plan to find one · ≤ 60 min aspirational, baseline set by the first unit (agent's recommendation; agent's first proposal — no instead-of recorded) — chosen
- Choice · Why: in context of no baseline, facing a graded metric story, we chose an aspirational target grounded in reading time over a hard gate, accepting it is an estimate.
- Cost accepted: the target may move after the first unit. · Reversibility: Type 2 · Confidence: low
- Revisit if: the partner shares freelance review times. · Evidence: R06, prd.md SC-001 · Interview line: "We measure our own baseline because nobody publishes one."
- Review: Topic Product · Weight ●●○ · One-liner: SC-001 ≤ 60 min per lesson, aspirational until baseline.

### D6 AI provider Anthropic, $30 build cap  [status: accepted]
- 2026-10-14 23:56 CDT · GI · M1–M2 · Decided by: human (GI "Yes, add QB-4/T-12 (eval against Newsela's published lessons). My GI answers: 1 default 2A 3A 4A 5 default 6 default 7A 8A, assumptions confirmed") · Proposed by: plan-product (claude-code, claude-opus-5-5) · .handoff/checkpoints/GI-M1.md@fb28ae0
- Context and forces: NFR-007, C-3; partner allows OpenAI or Anthropic (REQ-11)
- Options: Do nothing (no generation) — rejected: demo cannot run · A Anthropic, $30 cap (agent's recommendation; agent's first proposal — no instead-of recorded) — chosen · B OpenAI, same cap — rejected: partner uses Claude Code; no extra benefit shown
- Choice · Why: in context of a partner that allows either provider, facing a spend limit, we chose Anthropic with a $30 cap over OpenAI to match the partner's own tooling, accepting single-vendor dependence for the build.
- Cost accepted: vendor lock for prompts; a cap may stop iteration. · Reversibility: Type 1 · Confidence: med
- Revisit if: the cap is hit before the demo unit is drafted. · Evidence: GI card §2 · Interview line: "We matched the partner's tooling and capped spend before writing a prompt."
- Review: Topic Infrastructure · Weight ●●● · One-liner: Anthropic for drafting and assist; $30 total, ≤ $0.50 per lesson.

### D7 Partner material stays private and paraphrased  [status: accepted]
- 2026-10-14 23:56 CDT · GI · M1–M2 · Decided by: human (GI "Yes, add QB-4/T-12 (eval against Newsela's published lessons). My GI answers: 1 default 2A 3A 4A 5 default 6 default 7A 8A, assumptions confirmed") · Proposed by: plan-product (claude-code, claude-opus-5-5) · .handoff/checkpoints/GI-M1.md@fb28ae0
- Context and forces: U-01, C-8
- Options: Do nothing / commit it (shown as "B commit it") — rejected: one-way leak in a public repo · A keep private, paraphrase (agent's recommendation; agent's first proposal — no instead-of recorded) — chosen
- Choice · Why: in context of a public repo, facing uncleared partner documents, we chose to keep them private over committing them to protect the partner, accepting that clones lack the sources.
- Cost accepted: a fresh clone must re-fetch sources. · Reversibility: Type 1 · Confidence: med
- Revisit if: the partner clears the material. · Evidence: GI card §3, D1 · Interview line: "Their material stays theirs; the repo only paraphrases it."
- Review: Topic Process · Weight ●●○ · One-liner: Partner docs never committed; repo paraphrases them (confirms D1).

### D8 Any signed-in reviewer may approve  [status: accepted]
- 2026-10-14 23:56 CDT · GI · M1–M2 · Decided by: human (GI "Yes, add QB-4/T-12 (eval against Newsela's published lessons). My GI answers: 1 default 2A 3A 4A 5 default 6 default 7A 8A, assumptions confirmed") · Proposed by: plan-product (claude-code, claude-opus-5-5) · .handoff/checkpoints/GI-M1.md@fb28ae0
- Context and forces: FR-014, FR-031, A-2
- Options: Do nothing — rejected: approval cannot be trusted · A any signed-in reviewer approves (agent's recommendation; agent's first proposal — no instead-of recorded) — chosen · B separate approver role — rejected: extra role and setup for no brief requirement · C two-person approval — rejected: slows SC-001
- Choice · Why: in context of the brief's "review staff … approve", facing a 2-day build, we chose single-reviewer approval with an audit trail over role or two-person schemes to keep review fast, accepting no segregation of duties.
- Cost accepted: a careless approval is caught only by history and reopen (SC-004). · Reversibility: Type 1 · Confidence: med
- Revisit if: SC-004 reopen share exceeds 5 %. · Evidence: GI card §4, prd.md A-2 · Interview line: "Anyone on the review staff can approve, and every approval is on the record."
- Review: Topic Security · Weight ●●● · One-liner: No separate approver role; history records who approved.

### D9 Public GitLab repo with GitHub mirror  [status: accepted]
- 2026-10-14 23:56 CDT · GI · M1–M2 · Decided by: human (GI "Yes, add QB-4/T-12 (eval against Newsela's published lessons). My GI answers: 1 default 2A 3A 4A 5 default 6 default 7A 8A, assumptions confirmed") · Proposed by: plan-product (claude-code, claude-opus-5-5) · .handoff/checkpoints/GI-M1.md@fb28ae0
- Context and forces: REQ-12, U-03
- Options: Do nothing (no remote) — rejected: no CI, no MR, nothing to submit · A public (agent's recommendation; agent's first proposal — no instead-of recorded) — chosen · B private until submission — rejected: kickoff recipe is public
- Choice · Why: in context of the standing kickoff recipe, facing a graded submission, we chose a public repo over private-until-submission so reviewers can see the work, accepting that every commit is public.
- Cost accepted: every commit is public, so partner material must never be committed (D7). · Reversibility: Type 1 · Confidence: med
- Revisit if: the partner asks for privacy. · Evidence: GI card §7, memory partner-project-kickoff · Interview line: "The work is public from day one, so the partner can watch it grow."
- Review: Topic Infrastructure · Weight ●●○ · One-liner: Public repo on labs.gauntletai.com, mirrored to GitHub.

### D10 Draft every numbered lesson type, with ELD supports  [status: accepted]
- 2026-10-14 23:56 CDT · GI · M1–M2 · Decided by: human (GI "Yes, add QB-4/T-12 (eval against Newsela's published lessons). My GI answers: 1 default 2A 3A 4A 5 default 6 default 7A 8A, assumptions confirmed") · Proposed by: plan-product (claude-code, claude-opus-5-5) · .handoff/checkpoints/GI-M1.md@fb28ae0
- Context and forces: FR-005, A-1, A-3, NG-3
- Options: Do nothing — rejected: no scope · as recommended (agent's recommendation; agent's first proposal — no instead-of recorded) — chosen
- Choice · Why: in context of an outline with numbered lessons and flex rows, facing a short build, we chose every numbered type with ELD supports over a subset to match published lessons, accepting more prompt work.
- Cost accepted: more prompt variants. · Reversibility: Type 2 · Confidence: med
- Revisit if: drafts for one type keep failing checks. · Evidence: GI card §5, R02 · Interview line: "We draft every real lesson the outline numbers, the way their published lessons look."
- Review: Topic Product · Weight ●●○ · One-liner: Spark, Reading, Writing, Discussion, Showcase drafted; flex and assessments skipped.

### D11 Two-day build, US Central, no portal deadline  [status: accepted]
- 2026-10-14 23:56 CDT · GI · M1–M2 · Decided by: human (GI "Yes, add QB-4/T-12 (eval against Newsela's published lessons). My GI answers: 1 default 2A 3A 4A 5 default 6 default 7A 8A, assumptions confirmed") · Proposed by: plan-product (claude-code, claude-opus-5-5) · .handoff/checkpoints/GI-M1.md@fb28ae0
- Context and forces: C-6, REQ-14
- Options: Do nothing — rejected: no timebox · default (agent's recommendation; agent's first proposal — no instead-of recorded) — chosen
- Choice · Why: in context of a 1–2 day brief with no submission date, facing scope pressure, we chose a two-day box to cut scope rather than slip, accepting the cut order.
- Cost accepted: US-4–US-7 may be cut. · Reversibility: Type 2 · Confidence: med
- Revisit if: the portal shows a deadline. · Evidence: GI card §1 · Interview line: "Two days, then we cut scope, never extend."
- Review: Topic Process · Weight ●○○ · One-liner: Appetite two days from the start of M4.

### D12 Whole unit drafted within 60 minutes  [status: accepted]
- 2026-10-14 23:56 CDT · GI · M1–M2 · Decided by: human (GI "Yes, add QB-4/T-12 (eval against Newsela's published lessons). My GI answers: 1 default 2A 3A 4A 5 default 6 default 7A 8A, assumptions confirmed") · Proposed by: plan-product (claude-code, claude-opus-5-5) · .handoff/checkpoints/GI-M1.md@fb28ae0
- Context and forces: NFR-002, R05
- Options: Do nothing — rejected: no target · 60 minutes (agent's recommendation; agent's first proposal — no instead-of recorded) — chosen
- Choice · Why: in context of a few minutes per lesson, facing 41 lessons, we chose 60 minutes per unit to force parallel drafting, accepting provider rate limits as the risk.
- Cost accepted: parallel drafting needed. · Reversibility: Type 2 · Confidence: med
- Revisit if: rate limits make it unreachable. · Evidence: GI card §6, R05 I6 · Interview line: "A unit drafts over lunch, not overnight."
- Review: Topic Product · Weight ●○○ · One-liner: NFR-002 target 60 minutes per 41-lesson unit.

### D13 Draft the partner email for the human to send  [status: accepted]
- 2026-10-14 23:56 CDT · GI · M1–M2 · Decided by: human (GI "Yes, add QB-4/T-12 (eval against Newsela's published lessons). My GI answers: 1 default 2A 3A 4A 5 default 6 default 7A 8A, assumptions confirmed") · Proposed by: plan-product (claude-code, claude-opus-5-5) · .handoff/checkpoints/GI-M1.md@fb28ae0
- Context and forces: U-06
- Options: Do nothing — rejected: open questions stay guesses · A draft it (agent's recommendation; agent's first proposal — no instead-of recorded) — chosen
- Choice · Why: in context of open partner-only questions, facing a short build, we chose a drafted email over guessing, accepting a reply may come late.
- Cost accepted: none. · Reversibility: Type 2 · Confidence: med
- Revisit if: no reply before M4. · Evidence: GI card §8 · Interview line: "We asked the partner the questions only they can answer."
- Review: Topic Process · Weight ●○○ · One-liner: Three clarifying questions drafted; the human sends.

### D14 Evaluate drafts against published partner lessons  [status: accepted]
- 2026-10-14 23:56 CDT · GI · M1–M2 · Decided by: human (GI "Yes, add QB-4/T-12 (eval against Newsela's published lessons). My GI answers: 1 default 2A 3A 4A 5 default 6 default 7A 8A, assumptions confirmed") · Proposed by: plan-product (claude-code, claude-opus-5-5) · .handoff/checkpoints/GI-M1.md@fb28ae0
- Context and forces: decode QB-4, T-12, FR-034, SC-003
- Options: Do nothing — rejected: "drafts are good" stays a claim · add QB-4/T-12 and an evaluation run (agent's recommendation, raised after the GI card; agent's first proposal — no instead-of recorded) — chosen
- Choice · Why: in context of human-written lessons on the partner's review site, facing an unproven quality claim, we chose a measured comparison against those lessons over self-checks alone, accepting extra build work in M4.
- Cost accepted: M4 grows by one FR. · Reversibility: Type 2 · Confidence: med
- Revisit if: published lessons cannot be used as references. · Evidence: human GI reply, R02 · Interview line: "We grade our drafts against the lessons their own team wrote."
- Review: Topic Product · Weight ●●● · One-liner: FR-034: drafts scored against held-out published lessons by type.
