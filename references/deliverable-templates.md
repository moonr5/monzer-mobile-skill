# Deliverable templates

Write every file under `<WORKSPACE>/docs/` unless a path says otherwise.  
Fill every column. Use `UNKNOWN` + a row in `OPEN_QUESTIONS.md` — never invent a name.

## docs/ASSUMPTIONS.md

```
| ID | Decision | Safer alternative rejected | Why this is safer | Reversible? |
| --- | --- | --- | --- | --- |
```

## docs/OPEN_QUESTIONS.md

```
| ID | Question | Blocking? | Default used until answered |
| --- | --- | --- | --- |
```

## docs/BLOCKERS.md

```
| ID | Phase | What is blocked | Why | Workaround in use | Unblock condition |
| --- | --- | --- | --- | --- | --- |
```

## docs/SYSTEM_INVENTORY.md

One subsection each: Modules, Pages, API endpoints, Tables, Roles, Permissions, Integrations, Background jobs, Notification channels, Events.

```
### API endpoints
| Method | Path | Auth | Roles | Request | Response | Source file |
```

```
### Tables
| Table | Key columns | RLS / tenant column | Written by | Source file |
```

```
### Roles
| Role | Who in real life | Sees | Cannot see | Source file |
```

## docs/MOBILE_SCOPE_MATRIX.md

One row per (web feature × role). Decision must be one of: `MOBILE_FULL` | `MOBILE_LITE` | `WEB_ONLY` | `NOT_NEEDED`.

```
| Feature | Role | Decision | Reason (one line) | User context (counter/field/HQ) | Source |
```

## docs/DATA_PARITY_MATRIX.md

```
| Mobile screen | Reads (endpoint/table) | Writes | Permission | Sync (push/realtime/poll/focus) | Web counterpart |
```

## docs/API_GAP_LIST.md

```
| ID | Gap | Needed by screen | Proposed contract | Idempotency? | Status TODO/DONE/BLOCKED |
```

## docs/EXISTING_STACK_REPORT.md

Required headings: Runtime, Navigation, Styling, Server state, Local state, Auth, Tests, CI, Existing mobile code, Libraries chosen, Keep/change table.

```
| Piece | Found (version + path) | Keep or change | Why |
```

Greenfield Expo default if nothing exists: Expo Router + TanStack Query + Zustand + Zod + one styling system.

## docs/BUSINESS_INTENT_CHECK.md

```
| Intent | EXISTS / PARTIAL / MISSING | Evidence paths | What mobile will do |
```

Intents to score (override with system evidence): cross-store customer timeline; store inventory including other brands; display slots + replacement; dealer chat-first tool with own-data-only; language/formats from the system (Indonesian SMP/SMA if that is the market).

## docs/USER_JOURNEYS.md

For each role: situation, trigger, steps, failure/offline branch, success. Must include the demo scenario adapted to what the system actually has: two-store purchase → one HQ timeline; empty slot → other brand fills it; low stock → recommended order → chat approve with credit check.

## docs/NAVIGATION_MAP.md

```
| Role | Tabs (max 5) | Stacks / sheets | Entry route | Deep links |
```

## docs/SCREEN_INVENTORY.md

```
| Screen | Purpose | Roles | Data source (parity row) | Primary action | States: loading empty error offline no-permission success partial slow |
```

Every state cell is `designed` or `n/a` with reason. No blank cells.

## docs/CONTENT_GUIDE.md

Required headings: Language + reading level, Glossary, Tone, Formats (number/currency/date from system), Error pattern (`what happened` + `what to do`), Empty-state pattern.

## docs/DESIGN_SYSTEM.md

Required headings: Design read (one sentence), Dials (`DESIGN_VARIANCE`, `MOTION_INTENSITY`, `VISUAL_DENSITY`), Token table (name → value → usage), Type scale, Component list, Light/dark, Motion, What was rejected as generic.

## docs/ARCHITECTURE.md

Required headings: Module map, Navigation choice + why, State split, API client, Auth, Offline/conflict rule, Envs, CI, Secrets policy.

## docs/SECURITY_REPORT.md

```
| MASVS item | PASS / FAIL / N/A | Evidence | Fix if FAIL |
```

Cover at least: secure storage, no secrets in bundle, TLS, root/jailbreak handling, screenshot masking, clipboard/log hygiene, deep-link validation, input validation, dependency audit, least privilege, cross-tenant isolation test.

## docs/TEST_REPORT.md

```
| Requirement | Test type | File | Last run | Result | Notes |
```

## docs/PERFORMANCE_REPORT.md

```
| Metric | Budget | Device | Measured | Pass? | Evidence |
```

Required metrics: cold start, list FPS, scan latency, chat TTFT (if chat exists), memory, battery sample.

## docs/HANDOVER.md

Required headings: What was built, Verified with evidence, UNVERIFIED, Blockers still open, Risks, Next steps, How to run web + mobile side by side.

## App code locations (not under docs/)

| Artifact | Default path if greenfield | Rule if repo already exists |
| --- | --- | --- |
| Routes | `src/app/` | Keep existing router root |
| Screen bodies | `src/screens/<feature>/` | Keep existing |
| Shared UI | `src/components/` | Keep existing |
| Tokens | `src/theme/` | Extend the existing theme only |
| API client + Zod | `src/api/` | Keep existing client; add schemas |
| Feature modules | `src/features/<name>/` | Match existing module layout |
