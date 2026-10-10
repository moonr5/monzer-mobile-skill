---
name: quality
description: Run Quality Management, Quality Assurance, Quality Control, and Quality Improvement on a Monzer app. Use before calling any track done, and whenever a screen, build, or release needs a pass/fail on evidence.
---

# Quality — QM, QA, QC, QI

Load this leaf before the track is called done. Write one file: `WORKSPACE/docs/QUALITY.md`. Use the headings in `SKILL_ROOT/references/deliverable-templates.md`.

Four jobs. Do not merge them into "we tested it."

| Job | Question | When |
| --- | --- | --- |
| **QM** Quality Management | What must pass before anyone ships? | First, right after the track is chosen |
| **QA** Quality Assurance | Did we follow that process? | At the end of each phase, before the next phase |
| **QC** Quality Control | Does the product meet the spec? | On the built screens and flows, on evidence |
| **QI** Quality Improvement | What changes so this defect cannot return? | For every Critical and Major defect |

## Roles

Use these names in `QUALITY.md`. One agent may hold all four. The vetoes still apply.

| Role | Fights for | Veto |
| --- | --- | --- |
| Quality Manager | The plan, the gates, the release decision | Shipping with an open Critical defect or a failed QA gate |
| QA Lead | Process was followed before the work was called done | A phase marked `DONE` with no process check |
| QC Inspector | The product, judged from outputs | A pass based on the builder's claim instead of evidence |
| QI Lead | Root cause and a new check | Closing a Critical or Major with only a patch and no preventive check |

## 1. QM — write the plan first

Fill `## QM` before feature work (Track S: before screens; Track P / BOTH: during M0).

Record:

- Quality policy, one sentence: what "ship" means on this track.
- In-scope platforms (iOS, Android, web) and the demo journey.
- Gates that apply. Mark `N/A` with a reason when a gate does not apply.

| Gate | Track S | Track P / BOTH | Pass rule |
| --- | --- | --- | --- |
| Feeling + DNA before pixels | Required | Required | Statement and DNA Card exist |
| Design rubric | Required | Required at M2 | ≥85/100, no category under 7 |
| Screen states | Required | Required | loading, empty, error, offline, disabled, pressed, success |
| One system | N/A unless a backend exists | Required | Same accounts, API, database. No second client stack |
| MASVS | N/A for a prototype with no accounts | Required at M6 | `SECURITY_REPORT.md` has no open Critical |
| Tests | Prototype interactions work | Required at M7 | `TEST_REPORT.md` rows were run, or `UNVERIFIED` |
| Performance | N/A for a static mock | Required at M8 | Budgets in `PERFORMANCE_REPORT.md` |
| Release demo | Showcase board | Required at M10 | Script ran 3× or the misses are defects |

Release rule: the Quality Manager sets `RELEASE = HOLD` or `RELEASE = GO`. `GO` is allowed only when every applicable gate is PASS and every Critical QC defect is closed.

## 2. QA — check the process

Fill `## QA` at the end of each phase. A row is PASS only when the evidence exists.

| Check | PASS when |
| --- | --- |
| Track | `TRACK` is printed and the work matches it |
| Order | This phase's template headings exist before the next phase started |
| Design order | Feeling Statement and DNA Card were written before visual decisions |
| Stack | No second navigation, state, styling, or data library was added |
| Secrets | No API keys, DB credentials, or provider keys in the app |
| Scope | Every in-scope screen is in `SCREEN_INVENTORY.md` or the studio screen list, with states |
| Evidence | PROGRESS evidence is a path, command, or `UNVERIFIED` — never "done" with a blank cell |
| Copy | No lorem, "Item 1", or "Welcome back, User" |

A FAIL blocks the phase. Fix the process, re-check, then continue. Do not skip ahead.

## 3. QC — inspect the product

Fill `## QC` from the actual UI and test output. Read screenshots, logs, and test files. Do not grade from a description of what was intended.

Fail the check immediately when you see any of these:

- Red error screen, blank screen, or the app never opened
- Text overflow, clipped controls, or content under the home indicator
- Contrast or touch-target failure on a primary action
- A control that does not show pressed, disabled, loading, empty, error, or offline
- Track P: a screen on mock data, or a write that does not appear on the web client
- A journey that passes on one required platform and fails on the other

Log every defect:

```
| ID | Severity | Where | Evidence | Owner |
| QC-01 | Critical / Major / Minor | screen or journey | file, screenshot, or command | QC |
```

- **Critical** — crash, data loss, wrong account's data, cannot finish the primary journey, secrets in the app. Blocks release.
- **Major** — wrong state, broken primary action, a11y block on a primary control, failed rubric category. Blocks release until fixed or explicitly accepted by the user in `OPEN_QUESTIONS.md`.
- **Minor** — polish. May ship. Still goes to QI if the same minor appears twice.

Re-inspect after the fix. Update the row. Do not delete the original evidence.

## 4. QI — stop the repeat

Fill `## QI` for every Critical and Major, and for any defect that appears twice.

```
| Defect | Root cause | Correction | Preventive check added to QA | Re-inspected |
| QC-01 | | | | PASS / FAIL |
```

Root cause is why the process let it through (missing state in the inventory, no test, DNA ignored), not only the line that was wrong.

Add the new preventive check as a row in `## QA` before closing the defect.

## Done

`QUALITY.md` has all four headings. `RELEASE` is `GO` or `HOLD`. PROGRESS rows Q0–Q3 are `DONE` or `BLOCKED` with a reason. A track is not done while `RELEASE = HOLD`.
