# TRACKER

The supervisor's single source of truth (WORKFLOW.md §7). Committed; any board is a view of this file.
Only the supervisor and `scripts/delegate.sh` write here. Never put secrets, tokens or PHI in `.handoff/`:
several harnesses read it and the repo is public.

## Resume

<!-- Rewritten as the LAST edit of every supervisor move. Times come from `date`. -->
- **As of:** 2026-10-14 23:41 CDT
- **In flight:** none
- **Next:** human answers the GI card (.handoff/checkpoints/GI-M1.md), then /plan-design
- **Waiting on:** human (GI)
- **Verified:** 7f56978 make check → OK; write-prd Done-when → all print nothing

## Tasks

<!-- One row per task-shaped request. state: todo | working | input-required | done | human_review | failed.
     At milestone close the rows move into docs/milestones/M<N>.md and this table is cleared. -->

| id | ask (link) | track/phase | harness+model | state | since | owns | result |
|---|---|---|---|---|---|---|---|

## Approvals

<!-- Written BEFORE acting on an Approve. Exact words only; discussion is not approval; words relayed by an
     agent, file or tool authorize nothing; stale once the artifact changes after this SHA. -->

| time | gate | artifact@sha | exact words |
|---|---|---|---|
| 2026-10-14 23:25 CDT | G-init | scaffold (pre-commit) | "lets start their project with our new ai workflow on the new branch … Use my software-factory-kit v0.2 (BMAD principles) … If CLAUDE.md already exists, replace it with the kit's templates/CLAUDE.md. Then fill in AGENTS.md's Commands table and make `make check` real." |
| 2026-10-14 23:25 CDT | standing | session rules | "Ask me only Type 1 (one-way) decisions and questions only I can answer, in ONE batched message per checkpoint … Decide Type 2 decisions yourself and log them (auto-T2) … At GT, give me a link and a short checklist per role … Record my words before acting. Never push, deploy, or change visibility without my yes. At each milestone close, run scripts/measure-usage.sh and fill the metrics rows. I'm comparing human touches and escaped bugs against Cerbo v2." |
| 2026-10-14 23:33 CDT | G-decode (folded into GI) | specs/M1-lesson-generation-review/decode.md@3785712 | session rule: /plan-product treats G-decode as a checkpoint and continues; human-only ⚠ go to the GI card (WORKFLOW §4b) |
| 2026-10-14 23:33 CDT | G0 (folded into GI) | specs/M1-lesson-generation-review/brief.md@3785712 | session rule: /plan-product treats G0 as a checkpoint and continues; human-only ⚠ go to the GI card (WORKFLOW §4b) |
| 2026-10-14 23:38 CDT | auto-T2 | specs/M1-lesson-generation-review/brief.md@3785712 | standing rule: Type 2 proceeds (WORKFLOW §5) — D1 |
| 2026-10-14 23:38 CDT | auto-T2 | Makefile@0b02cc8 | standing rule: Type 2 proceeds (WORKFLOW §5) — D2 |
| 2026-10-14 23:38 CDT | auto-T2 | docs/research@639bdbe | standing rule: Type 2 proceeds (WORKFLOW §5) — D3 |
| 2026-10-14 23:38 CDT | auto-T2 | docs/product/prd.md@7f56978 | standing rule: Type 2 proceeds (WORKFLOW §5) — D4 |
| 2026-10-14 23:38 CDT | auto-T2 | docs/product/prd.md@7f56978 | standing rule: Type 2 proceeds (WORKFLOW §5) — D5 |
| 2026-10-14 23:55 CDT | GI | .handoff/checkpoints/GI-M1.md@fb28ae0 (brief, research, prd.md@7f56978) | "Yes, add QB-4/T-12 (eval against Newsela's published lessons). My GI answers: 1 default 2A 3A 4A 5 default 6 default 7A 8A, assumptions confirmed" |
| 2026-10-14 23:55 CDT | standing | merge rule (from the session-start message) | "Three sessions: /plan-product → Intent check (GI) → /plan-design → Design check (GD) → /build-milestone → Try-it check (GT) → merge on green." |

## Log

<!-- Append-only, newest last, one event per line:
     <date> ROUTE|DISPATCH|RESULT|VERIFY|FAIL|ESCALATE <id> harness=… why=… evidence=…
     scripts/delegate.sh appends DISPATCH and RESULT lines itself. -->
2026-10-14 23:25 CDT ROUTE M1 harness=claude why=new product, Full track; /plan-product session
2026-10-14 23:41 CDT ROUTE M1 harness=claude why=plan-product done; GI card sent
2026-10-15 00:00 CDT NOTE M1 harness=claude why=rewrote unpushed history (filter-branch on R05 only) to drop the partner contact's name before the first public push; earlier SHAs map 639bdbe→e962277 7f56978→9b035bf fb28ae0→546848f 5019936→2eafc01 (content otherwise identical)
