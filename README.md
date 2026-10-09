# Mobile App Builder

**One master skill. Two tracks.**

- **Studio** — "make me an app", screens, mockup, prototype. A $26M-class studio. Feeling first. Never the same look twice.
- **Production** — Expo client of your **existing** web system. Same accounts, same API, same database.
- **Both** — unique studio design, then wired to the real backend.

Do not run `npx skills add`. The 23 leaf skills are already inside `skills/`.

![One system, one data](docs/images/hero-one-system.jpg)

<p align="center"><img src="docs/images/one-system.svg" alt="Web and mobile share one backend and one database" width="920"></p>

---

## Start in one picture

<p align="center"><img src="docs/images/agent-loop.svg" alt="Read SKILL.md, print two paths, copy PROGRESS, start M0" width="920"></p>

```mermaid
flowchart LR
  A[Read SKILL.md] --> B[Set SKILL_ROOT + WORKSPACE]
  B --> T{Track?}
  T -->|Studio| S[design-studio 0-9]
  T -->|Production| P[M0 to M10]
  T -->|Both| S2[Studio 0-6]
  S2 --> P
  S --> G[SHOWCASE + BRIEF]
  P --> H[HANDOVER.md]
```

**Paste this to any agent** (Cursor, Claude Code, Codex, Copilot):

```
Read this file fully and obey it as the only workflow:
https://raw.githubusercontent.com/moonr5/monzer-mobile-skill/main/SKILL.md

Or clone the repo and set SKILL_ROOT to that folder.
WORKSPACE = this product repo (existing web app + backend).

Execute M0 through M10 without stopping.
Write docs under WORKSPACE/docs/.
```

Install into your own skills folder: see [INSTALL.md](INSTALL.md).

---

## The 11 phases

<p align="center"><img src="docs/images/phases-m0-m10.jpg" alt="Phase strip M0 to M10" width="920"></p>
<p align="center"><img src="docs/images/phases.svg" alt="M0 Discover through M10 Demo" width="920"></p>

```mermaid
flowchart LR
  M0[M0 Discover] --> M1[M1 Journeys]
  M1 --> M2[M2 Design]
  M2 --> M3[M3 Architecture]
  M3 --> M4[M4 Features]
  M4 --> M5[M5 Backend]
  M5 --> M6[M6 Security]
  M6 --> M7[M7 Tests]
  M7 --> M8[M8 Perf]
  M8 --> M9[M9 Release]
  M9 --> M10[M10 Demo]
```

| | What you see | What gets written |
| --- | --- | --- |
| **M0** | The real web system | 6 discovery files |
| **M1** | Who uses the phone, and where | journeys, nav, screens, copy |
| **M2** | A distinctive native design system | tokens + components + gallery |
| **M3** | Auth, API client, offline queue | `ARCHITECTURE.md` |
| **M4** | Every in-scope screen, wired | real backend, no mocks |
| **M5** | Missing mobile APIs | on the **existing** backend |
| **M6** | MASVS review | `SECURITY_REPORT.md` |
| **M7** | Jest + Maestro + web↔phone parity | `TEST_REPORT.md` |
| **M8** | Measured on a mid-range phone | `PERFORMANCE_REPORT.md` |
| **M9** | Stores, OTA, icons | EAS production |
| **M10** | 10-minute CEO demo, 3 clean runs | `HANDOVER.md` |

---

## What is inside this one skill

<p align="center"><img src="docs/images/skill-pack.jpg" alt="Master skill with clustered leaves" width="920"></p>
<p align="center"><img src="docs/images/skill-tree.svg" alt="Expo, Design, Quality, Ship, Rules" width="920"></p>

```mermaid
flowchart TB
  MASTER[SKILL.md master]
  MASTER --> EXPO[Expo · UI · data · router]
  MASTER --> DESIGN[mobile-design · frontend-design · theming]
  MASTER --> QUALITY[testing · best-practices · RN skills]
  MASTER --> SHIP[EAS · local-build · app-icon]
  MASTER --> RULES[one DB · MASVS · PROGRESS.md]
```

Full visual map with clickable mermaid: [docs/VISUAL.md](docs/VISUAL.md).

---

## Golden rule

```mermaid
flowchart LR
  WEB[Existing web app] --- API[Existing backend]
  PHONE[iOS + Android] --- API
  API --- DB[(Existing database)]
```

- Same login. Same permissions. Changes appear on the other client within seconds.
- No second database. No API keys in the app.
- If mobile needs an endpoint, add it to the existing backend.

---

## Repo map

```
SKILL.md                 ← agents start here
AGENTS.md                ← Codex / AGENTS.md hosts
INSTALL.md               ← Cursor, Claude Code, Copilot
docs/images/             ← posters + SVG diagrams
docs/VISUAL.md           ← interactive mermaid map
references/              ← PROGRESS + deliverable templates
skills/                  ← 23 bundled leaves
```
