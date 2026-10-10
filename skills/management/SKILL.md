---
name: management
description: Run Monzer as a managed build. Load this first after the track is chosen. It sets the order of work, who owns release, and which efficiency tool to open only when the work is blocked.
---

# Management

Load this once, right after `TRACK` is printed. Then run the track. Do not load every leaf up front. A leaf is opened when its row in `SKILL.md` matches the task you are in.

## Order

1. `docs/PROGRESS.md` is the plan. One row is `DOING`. Finish it or mark it `BLOCKED` before the next row.
2. Load `skills/quality/SKILL.md` and write the QM gates before feature work. That is the management system. QA, QC, and QI stay inside that file.
3. After the risk rows exist, load `skills/qe/agents/fmea-reviewer/SKILL.md` and fix the gaps it names. Skip factory control plans and PPAP. A missing test for a primary journey is a gap.
4. Build the phase you are in. Open only the leaf that phase names.
5. At M9 (or the studio handoff), load `skills/release-management/SKILL.md`, then the EAS leaves. `RELEASE = GO` from `QUALITY.md` is required before a store build.
6. At M10, load `skills/documentation/SKILL.md` and write `HANDOVER.md` from evidence. No claim without a path or a command.

## Efficiency

The default is the smallest tool that finishes the current row.

| Situation | Open this | Do not |
| --- | --- | --- |
| A screen or command fails and you do not know why | `skills/debugging-assistant/SKILL.md` | Guess a second library |
| M8 budget fails after a real measurement | `skills/react-native-best-practices/SKILL.md`, then `skills/performance-optimization/SKILL.md` | Optimize before the number exists |
| A QC defect is a structural code smell | `skills/refactoring-expert/SKILL.md` on that defect only | Rewrite a working module |
| Release checklist, version, changelog | `skills/release-management/SKILL.md` | Ship on `RELEASE = HOLD` |
| README, API notes, runbook | `skills/documentation/SKILL.md` | Leave M10 as bullet fragments |

Change one thing, re-check, then continue. Record the result on the PROGRESS row before starting another tool.

## Release authority

The Quality Manager sets `RELEASE`. Management does not override a Critical defect. A blocked row has a reason in `BLOCKERS.md` and a workaround. The track is finished only when every row on that track is `DONE` or `BLOCKED` and `HANDOVER.md` exists.
