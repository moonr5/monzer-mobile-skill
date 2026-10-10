---
name: quality
description: End-to-end quality system for a Monzer app. Runs Quality Management, Quality Assurance, Quality Control, and Quality Improvement using the bundled leaves. Use before calling any track done, and whenever a screen, build, or release needs a pass/fail on evidence.
---

# Quality system — QM, QA, QC, QI

This file is the only entry. Load a leaf only for the job you are in. Write `WORKSPACE/docs/QUALITY.md` with the headings in `references/deliverable-templates.md`.

Leaf paths are under `SKILL_ROOT`. Do not install them from GitHub.

| Job | Question | Leaf to read |
| --- | --- | --- |
| **QM** | What must pass before ship, and is that system being followed? | This file §1, then `skills/qe/risk-analysis/dfmea-design/SKILL.md` and `skills/qe/audit/iso-9001-internal-audit/SKILL.md` |
| **QA** | Did we build the right checks before the work was called done? | `skills/qa-testing/SKILL.md`, then `skills/qe/planning/dvp-test-plan/SKILL.md` |
| **QC** | Does the product meet the spec, on evidence? | `skills/critique-review/SKILL.md`, then `skills/qe/documentation/ncr-writing/SKILL.md` |
| **QI** | What changes so this defect cannot return? | §4 below. Pick one method. Do not run all of them. |

Automotive-only methods (PPAP, IATF, VDA, gauge R&R, supplier PPAP, factory control plans) are not bundled. If a leaf links to `control-plan`, add the preventive check to `## QA` instead. Apply ISO and FMEA language to this app: screens, API, auth, offline sync, and store release.

## Roles

| Role | Fights for | Veto |
| --- | --- | --- |
| Quality Manager | Gates, audit, release decision | `RELEASE = GO` with an open Critical or a failed gate |
| QA Lead | Test strategy exists before the code is called done | A phase `DONE` with no process check |
| QC Inspector | Product judged from outputs | A pass based on the builder's claim |
| QI Lead | Root cause and a preventive check | Closing Critical or Major with only a patch |

## 1. QM — plan, then audit

Fill `## QM` before feature work (Track S: before screens. Track P / BOTH: during M0).

Record the quality policy in one sentence, the platforms, the demo journey, and this gate table. Mark a gate `N/A` only with a reason.

| Gate | Track S | Track P / BOTH | Pass rule |
| --- | --- | --- | --- |
| Feeling + DNA before pixels | Required | Required | Statement and DNA Card exist |
| Design rubric | Required | Required at M2 | ≥85/100, no category under 7 |
| Risk register | Required | Required | One DFMEA-style row per primary journey |
| Screen states | Required | Required | loading, empty, error, offline, disabled, pressed, success |
| One system | N/A unless a backend exists | Required | Same accounts, API, database |
| MASVS | N/A for a prototype with no accounts | Required at M6 | No open Critical in `SECURITY_REPORT.md` |
| Verification plan | Required | Required before M4 | DVP rows link each risk to a test |
| Tests | Prototype interactions work | Required at M7 | Runs cited, or `UNVERIFIED` |
| Performance | N/A for a static mock | Required at M8 | Budgets in `PERFORMANCE_REPORT.md` |
| Release demo | Showcase board | Required at M10 | Script ran 3×, or each miss is a defect |

Then load `skills/qe/risk-analysis/dfmea-design/SKILL.md`. Write one risk row per primary journey (wrong account data, lost offline write, broken primary action, secret in the app). Use `skills/qe/risk-analysis/action-priority-ap/SKILL.md` only to rank those rows. Load `skills/qe/agents/fmea-reviewer/SKILL.md` and close the gaps it reports before feature work.

Before `RELEASE = GO`, load `skills/qe/audit/iso-9001-internal-audit/SKILL.md` and `skills/qe/agents/audit-guide/SKILL.md`. Audit only: documented gates, who inspected, nonconformities, corrective actions, and whether the demo is the release evidence. Record the audit result in `## QM`.

`RELEASE = GO` only when every applicable gate is PASS and every Critical QC defect is closed. Otherwise `RELEASE = HOLD`.

## 2. QA — prevent

At the end of each phase, fill `## QA`.

Load `skills/qa-testing/SKILL.md` once, before M4 (Track S: before the screen set). Write the test strategy into `## QA`: unit, component, integration, Maestro e2e, and the web↔phone parity check on Track P.

Load `skills/qe/planning/dvp-test-plan/SKILL.md`. Each DFMEA row needs a verification row: test, pass/fail criterion, and where the evidence will be stored. A journey with no test is an open QA fail.

Process checks, PASS only with evidence:

| Check | PASS when |
| --- | --- |
| Track | `TRACK` is printed and the work matches it |
| Order | This phase's template headings exist before the next phase |
| Design order | Feeling Statement and DNA Card exist before visual decisions |
| Stack | No second navigation, state, styling, or data library |
| Secrets | No API keys or provider keys in the app |
| Scope | Every in-scope screen is listed with its states |
| Evidence | PROGRESS evidence is a path, command, or `UNVERIFIED` |

A FAIL blocks the phase. Fix, re-check, then continue.

## 3. QC — inspect

Fill `## QC` from the product, not from the plan.

Load `skills/critique-review/SKILL.md` on the diff or the feature folder. Findings become QC rows. Load `skills/critique-review/references/review-rubric.md` when the change touches auth, data, sync, or money.

Load `skills/qe/documentation/ncr-writing/SKILL.md` and write an NCR for every Critical and Major.

Fail immediately on: red error screen, blank screen, app never opened, overflow, clipped controls, contrast or touch-target failure on a primary action, missing required state, Track P screen still on mock data, or a journey that fails on one required platform.

```
| ID | Severity | Where | Evidence | Status |
| QC-01 | Critical / Major / Minor | screen or journey | file, screenshot, or command | Open |
```

- **Critical** — crash, data loss, wrong account's data, primary journey blocked, secret in the app. Blocks release.
- **Major** — wrong state, broken primary action, a11y block, failed rubric category. Blocks release until fixed or the user accepts it in `OPEN_QUESTIONS.md`.
- **Minor** — polish. May ship. Goes to QI if it appears twice.

Re-inspect after the fix. Keep the original evidence.

## 4. QI — stop the repeat

Fill `## QI` for every Critical and Major, and for any defect that appears twice.

1. Scope it with `skills/qe/problem-solving/is-is-not-scoping/SKILL.md`.
2. Find the cause with one method: `skills/qe/problem-solving/5why-root-cause/SKILL.md`. Add `skills/qe/problem-solving/fishbone-analysis/SKILL.md` only when the cause is still disputed. Use `skills/qe/agents/rca-facilitator/SKILL.md` when the 5-Why chain is circular or rests on "user error".
3. Respond: Critical or a field failure → `skills/qe/problem-solving/8d-problem-solving/SKILL.md` and `skills/qe/documentation/8d-report-writing/SKILL.md`. Any other improvement → `skills/qe/problem-solving/pdca-improvement/SKILL.md`. A defect that already came back → `skills/qe/problem-solving/dmaic/SKILL.md`. Several defects of the same type → `skills/qe/problem-solving/quality-problem-zeroing/SKILL.md`.
4. Open the record with `skills/qe/documentation/car-corrective-action/SKILL.md`.

```
| Defect | Root cause | Correction | Preventive check added to QA | Re-inspected |
```

Root cause is why the process let it through. Add that check to `## QA` before closing the row.

## Done

`QUALITY.md` has `## QM`, `## QA`, `## QC`, `## QI`, and `RELEASE = GO` or `RELEASE = HOLD`. PROGRESS Q0–Q3 are `DONE` or `BLOCKED`. The track is not done while `RELEASE = HOLD`.
