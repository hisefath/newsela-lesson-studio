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
