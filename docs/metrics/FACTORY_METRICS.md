# Factory metrics

One row per milestone, appended by `report-milestone` (numbers from `docs/milestones/M<N>.md` §8-§9).
The goal: fewer human touches per milestone with equal or fewer escaped defects (bugs found by using the app after
merge), while tokens and wall-clock stay measured. A Max plan bills no per-token cost, so tokens are the cost signal.

| Milestone | Wall-clock (h) | Human touches (prompts / approvals) | First-pass | Tokens in+cache / out | Escaped defects | Report |
|---|---|---|---|---|---|---|
| M1–M2 Newsela (/plan-product, kit v0.2) | 0.8 | 3 prompts / 1 approval (GI, one batched reply) | n/a (docs) | subagents 437,851 / 85,902; supervisor not separable (session cwd = workbench, shared with other sessions: 1,112,885+57.6M cache read / 199,478 for all workbench sessions in the window) | 0 (no app yet) | MR !1 |
