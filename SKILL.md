---
name: monzer
description: Design or build a unique iOS/Android/cross-platform mobile app, UI, screens, mockup, or prototype in any words ("make me an app for...", "design a fitness app", "screens for my delivery startup"). Also builds a production Expo client of an EXISTING web app so mobile and web share accounts and data. Runs Monzer's $26M-class design studio (feeling-first, never the same look twice) plus the M0-M10 engineering workflow. Use for mobile design, screens, prototypes, a production CRM/dealer/web-system app, or when the user says follow monzer or Monzer.
---

# Monzer — Mobile Design Studio and App Builder

Any AI agent can run this. There is no extra installer. **Do not run `npx skills add`.**  
Humans: start at [README.md](README.md) (images + diagrams). Agents: stay in this file.

## 0. AGENT CONTRACT — do this before anything else

### 0.1 Resolve two absolute paths
- **SKILL_ROOT** = the folder that contains *this* `SKILL.md` (sibling folders: `skills/`, `references/`).
- **WORKSPACE** = the product repo (existing web app, backend, database, optional mobile app). Usually the current working directory. Not SKILL_ROOT unless they are the same repo.

Print both paths in one short line, then continue. If SKILL_ROOT is unknown, search the workspace and user skill directories for `monzer/SKILL.md` or `monzer-mobile-skill/SKILL.md`.

### 0.2 Path rules
- Leaf skill `foo` means: read `SKILL_ROOT/skills/foo/SKILL.md`. Then read only the files *that* file names, resolving them under that leaf folder.
- When a leaf says "load expo-native-ui" (or any other leaf name), translate to `SKILL_ROOT/skills/<name>/SKILL.md`. Never look on GitHub. Never run `npx skills`.
- Templates: `SKILL_ROOT/references/progress-template.md` and `SKILL_ROOT/references/deliverable-templates.md`.
- All workflow docs are written to `WORKSPACE/docs/`. App code is written in WORKSPACE, never inside SKILL_ROOT.

### 0.3 First-run bootstrap (or resume)
1. If `WORKSPACE/docs/PROGRESS.md` exists → read it. Resume at the first row whose status is not `DONE`. Do not restart finished work.
2. If it does not exist → copy the table from `SKILL_ROOT/references/progress-template.md` to `WORKSPACE/docs/PROGRESS.md`. Create empty `ASSUMPTIONS.md`, `OPEN_QUESTIONS.md`, `BLOCKERS.md` using the tables in `deliverable-templates.md`.
3. Mark B0–B3 `DONE` with the two absolute paths and the chosen track as evidence.
4. Load `skills/management/SKILL.md` once. Then start (or continue) the first non-DONE phase. Do not ask "should I continue?"

### 0.4 Non-stop protocol
1. Run the chosen track in order in one run. Track S: design-studio phases 0–9. Track P: M0 → M10. Track BOTH: studio 0–6, then M0 and M3–M10. Never skip a row on that track.
2. Impossible step → log in `BLOCKERS.md`, apply the safest workaround, mark `BLOCKED`, continue.
3. No TODOs, placeholders, lorem, mock-only screens, or half-built features in scope.
4. Ambiguity → safest assumption in `ASSUMPTIONS.md`, keep going. Ask the user only if a decision is irreversible AND could reasonably go either way; finish everything else first.
5. Never claim pass/verified unless you ran it. Otherwise `UNVERIFIED`.
6. Inspect before edit. No unnecessary rewrites. Preserve working behavior.
7. Job is done only when every FINAL DELIVERABLE exists and every PROGRESS row is `DONE` or `BLOCKED` with a reason.
8. After every task: update that PROGRESS row before starting the next.

### 0.5 Tools you may use
Use whatever tools your host gives you (read, write, shell, grep, browser). This skill does not require Cursor-only tools. Shell examples assume the WORKSPACE as cwd. Package installs: `npx expo install <pkg>` after you know the Expo SDK from `package.json`.

### 0.6 Pick a track (before M0 or studio Phase 0)
Print `TRACK = S | P | BOTH` then run that track without asking to confirm.

| Track | When | Then |
| --- | --- | --- |
| **S** Studio | Design, mockup, screens, prototype, "make me an app for…", "make it feel…", "again / different look". No existing backend in scope. | Read `skills/design-studio/SKILL.md` and run its phases 0–9. Write `docs/DNA_LEDGER.md`, `STUDIO_BRIEF.md`, `SHOWCASE.md`. |
| **P** Production | Existing web app / CRM / dealer platform / shared database. | This file's M0–M10. Still load design-studio for M1–M2 feeling + DNA so the UI is unique. Existing product name and brand win over invented names. |
| **BOTH** | Existing system AND the user wants a new look, screens, or prototype first. | Studio 0–6 (feeling, DNA, system, screens) then Production M0 and M3–M10. Do not invent a second product. |

"Same idea, completely different look" or "again" → stay on the current track, redraw the DNA Card (design-studio §4 and §11).

---

## ROLE
On Track S you are the named studio in `skills/design-studio/SKILL.md` (Creative Director, UI Lead, Critic, and the rest). On Track P / BOTH you are also principal mobile architect and Expo engineer: the web app, backend and database already exist; mobile is a first-class client of that system, not a separate product.

## QUALITY BAR
Treat design and engineering as a $120M-quality product: distinctive identity, zero rough edges, enterprise reliability. "Good enough" is a failure. (Quality standard, not a spending instruction.)

## SOURCE OF TRUTH
**Track S:** the brief and the Feeling Statement win. Infer freely; invent a name unless the user gave one.
**Track P / BOTH:** discover the real system from code, schema, APIs, auth, roles, jobs, notifications, docs, seed data, existing mobile. The system wins over this skill (including product name). Record differences in `ASSUMPTIONS.md`. Never invent names for terms you cannot find; use configurable labels and log them in `OPEN_QUESTIONS.md`.

Business intent to score in `BUSINESS_INTENT_CHECK.md` (build only what exists or is clearly missing and needed):
- HQ sees one customer across stores, with a cross-store purchase timeline.
- HQ sees store inventory (own + other brands), display slots (full/low/empty), what replaced an emptied slot, own vs competitor share.
- Dealers/staff get a simple chat-first tool and see only their own data.
- UI language: simple Indonesian at SMP/SMA level if that is the market; otherwise language and formats from the system.

## GOLDEN RULE — one system, one data set
Track P / BOTH only. Same accounts, same backend, same database as web. Same permissions. Changes appear on the other client within seconds. No second database. No DB credentials, service keys, or AI provider keys in the app. Missing mobile endpoints go on the existing backend (versioned, documented, tested) reusing web business logic. Server enforces authz; hiding UI is not the control.

## LEAF ROUTER
Read a leaf only when the current task needs it. This master wins on product, phases, and deliverables. A leaf wins on API/version details *after* you inspect the project.

| Task | Read first (`SKILL_ROOT/skills/…`) |
| --- | --- |
| After the track is chosen, before any phase | `management/SKILL.md` — order of work, release authority, which tool to open |
| Track S, or any unique look / feeling / mockup / screens | `design-studio/SKILL.md` first — then the leaves below |
| Any Expo/EAS question | `expo-overview/SKILL.md` then the leaf it names |
| New Expo folders only (no existing layout) | `expo-project-structure/SKILL.md` |
| M1 journeys / screens / UX | `design-studio/SKILL.md` then `mobile-design/SKILL.md` + `references/design-process.md`, `screen-patterns.md`, `navigation.md` |
| M2 identity | `design-studio/SKILL.md` then `frontend-design/SKILL.md` then `mobile-design/SKILL.md` |
| M2 tokens / components | `expo-design-system/SKILL.md` then `expo-native-ui`, `expo-ui`, `theming` |
| Motion / gestures | `expo-animation/SKILL.md` |
| Navigation | Existing stack first. Expo Router → `expo-router/SKILL.md`. React Navigation → `react-navigation/SKILL.md` |
| API / cache / offline / four screen states | `expo-data-fetching/SKILL.md` |
| Lists, images, press, compiler | `react-native-skills/SKILL.md` then the matching `rules/` file |
| Jank / TTI / bundle / memory | `react-native-best-practices/SKILL.md` then `performance-optimization/SKILL.md` |
| A failure you cannot explain | `debugging-assistant/SKILL.md` |
| A QC defect that is a structural code smell | `refactoring-expert/SKILL.md` on that defect only |
| Custom native build | `expo-dev-client/SKILL.md` |
| SDK upgrade | `expo-upgrade/SKILL.md` then `upgrading-react-native/SKILL.md` if bare RN |
| Component tests | `react-native-testing/SKILL.md` (v13 vs v14) |
| Maestro e2e | `maestro-mobile-testing/SKILL.md` |
| Accessibility (VoiceOver/TalkBack) | `react-native-accessibility/SKILL.md` |
| MASVS checklist / M6 | `masvs-checklist/SKILL.md` then `secure-storage-audit`, `auth-assessment`, `network-security-check` |
| Secrets in repo or bundle | `secrets-scan/SKILL.md` |
| AI chat / prompt injection | `prompt-injection-test/SKILL.md` |
| Web React → native Expo | `expo-web-to-native/SKILL.md` |
| Bare RN upgrade (not just Expo SDK) | `upgrading-react-native/SKILL.md` |
| Store submit / OTA / EAS CI | `release-management/SKILL.md` then `eas-app-stores`, `eas-update`, `eas-workflows` |
| Handover, README, API notes | `documentation/SKILL.md` |
| Local APK / sim .app | `local-build/SKILL.md` |
| Icons | `app-icon/SKILL.md` |
| Cloud simulator | `eas-simulator/SKILL.md` |
| Push / tap-to-open | `push-notifications/SKILL.md` |
| Camera / barcode scan | `camera-scan/SKILL.md` |
| Map / device location | `maps-location/SKILL.md` |
| Language, formats, RTL | `i18n-rtl/SKILL.md` then `mobile-design/references/adaptivity-localization.md` |
| Crashes (Sentry) | `sentry-react-native/SKILL.md` |
| Product analytics (Amplitude) | `amplitude-expo/SKILL.md` |
| QM / QA / QC / QI, before the track is called done | `quality/SKILL.md` — it loads `qa-testing`, `critique-review`, and `skills/qe/…` |

Mobile-design extra files live in `SKILL_ROOT/skills/mobile-design/references/`: `visual-system.md`, `typography-color.md`, `accessibility-touch.md`, `motion-haptics.md`, `forms.md`, `feasibility-risk.md`, `adaptivity-localization.md`, `platform-ios.md`, `platform-android.md`, `react-native-implementation.md`, `review-checklists.md`, `review-rules.md`.

**Stack conflicts:** inspect first. Never add a second navigation, state, styling, or data-fetching system. Greenfield Expo default: Expo Router + TanStack Query + Zustand + Zod + one styling approach, written in `ARCHITECTURE.md`. Prefer `@expo/ui` before a community kit; its List is a grouped settings list, not a virtualized feed (use FlashList/FlatList). Not bundled: TV, brownfield, App Clip, Expo DOM, Vercel hosting, Platano `ship`. Licenses: `ATTRIBUTION.md`.

## HARD RULES (always on)
**Expo.** Detect SDK from `package.json`. `npx expo install`. Do not bump SDK by hand. Do not restructure an existing app to match `expo-project-structure`.

**Design read (before any pixels):** write the Feeling Statement from `design-studio` §3, then the DNA Card (§4), then this line: `Reading this as: <category> for <audience>, with a <direction> interface, targeting iOS+Android.` Operational/dealer default dials: `DESIGN_VARIANCE=6`, `MOTION_INTENSITY=4`, `VISUAL_DENSITY=6` (lower for banking/health/safety) unless the DNA Card sets density/motion explicitly. Touch ≥44pt iOS / ≥48dp Android. WCAG AA (4.5:1 body, 3:1 large/UI). Safe areas, keyboard, edge-to-edge. Dynamic Type + Reduce Motion. Gestures need a visible alternative. Status never color-only. Required states: loading, empty, error, offline, disabled, pressed, success. One theme; screens import components; components import tokens.

**Refuse generic AI mobile.** Follow design-studio §4.4. No website heroes, glow blobs, purple-blue gradients, nested cards, random pills, fake glass, generic avatars, lorem, success-only UI, Inter/Roboto-only, "Welcome back, User", or five identical gray tab icons.

**M2 identity.** Load `design-studio` then `frontend-design`. Two passes only after Feeling + DNA exist. Append the DNA Card to `docs/DNA_LEDGER.md`. Never repeat more than 2 axes from an earlier card.

**Engineering defaults** (unless the repo already chose otherwise): FlashList for long lists; `expo-image`; `Pressable`; Reanimated on `transform`/`opacity` only; native stack/tabs; TanStack Query + Zustand + Zod; `expo-secure-store` for tokens (never AsyncStorage); text only inside `Text`; no falsy `&&` that can be `0`; no fat barrel imports; measure before memoizing.

**Quality.** Load `skills/quality/SKILL.md`. QM writes the gates first. QA checks the process at the end of each phase. QC inspects the product from evidence, not from a claim. QI adds a preventive check for every Critical and Major. Do not set `RELEASE = GO` while a Critical defect is open. Record it in `docs/QUALITY.md`.

**Copy.** Active voice, sentence case, user words. Errors = what happened + what to do. Empty = invite an action. Same verb from button through toast.

**Libraries.** Choose ONE styling/component approach. Record every add in `EXISTING_STACK_REPORT.md`. Vercel AI SDK is backend-only; never embed provider keys.

## PHASES
File shapes: `SKILL_ROOT/references/deliverable-templates.md`.  
Do not start phase N+1 until that template's required tables/headings exist for phase N (or the missing piece is `BLOCKED`).

### M0 Discovery — no app feature code yet
Read the whole web app, backend, schema, APIs, auth, roles, jobs, notifications, docs, seeds, existing mobile. Then write the six M0 docs. Scope hint (override with evidence): primary users = store counter; secondary = field/regional; HQ = light monitoring; heavy admin = `WEB_ONLY`.
**Done when:** M0.1–M0.6 are `DONE` and consistent with each other. Load `quality` and write the QM section of `QUALITY.md` (Q0) before M1.

### M1 Product / IA
Load `design-studio` (strategy, feeling, DNA, architecture) then mobile-design leaves. Write journeys, nav map, screen inventory (every state), content guide, `DNA_LEDGER.md`. Include the demo scenario adapted to the real system.
**Done when:** M1.1–M1.4 `DONE` and a DNA Card exists.

### M2 Design system
Load `design-studio` §§5–6, then frontend-design → expo-design-system → expo-native-ui → theming. Feeling + DNA first. Write the two-pass plan into `DESIGN_SYSTEM.md`. Implement tokens + components (buttons, inputs, search, list rows, cards, status chips with icon+text, stat tiles, simple charts, sheets, dialogs, toasts, segmented controls, skeletons, empty/error/offline, scan overlay, chat, timeline/tree, swipe cards). Load `camera-scan` when a screen scans, `maps-location` when a screen shows places, and `i18n-rtl` before writing new copy. Gallery in light and dark. Motion via expo-animation. Score with the $26M rubric before calling M2 done (85+/100, no category under 7). Load `quality` and record the QC score in `QUALITY.md`. Load `react-native-accessibility` for labels, roles, and touch targets.
**Done when:** M2.1–M2.4 `DONE`.

### M3 Architecture
Load expo-data-fetching + the navigation leaf + react-native-skills. Feature modules, typed API client, auth, offline queue, sync, EAS envs, CI. Write `ARCHITECTURE.md`.
**Done when:** M3.1–M3.6 `DONE`.

### M4 Features
Load `react-native-accessibility` while building UI. If the system has AI chat, load `prompt-injection-test` before shipping the assistant. If the existing product is a React web app being ported, load `expo-web-to-native` first. Build every `MOBILE_FULL` / `MOBILE_LITE` row, real backend, no mocks, in this order: (1) auth/roles/lock/profile (2) AI chat only if the system has it (3) counter flows (4) inventory (5) display slots (6) orders/credit/approvals (7) notifications — load `push-notifications` (8) timeline (9) HQ dashboards (10) loyalty only if system+scope (11) settings, including language via `i18n-rtl`. Load `camera-scan` or `maps-location` on the screen that needs them. Each screen: all states, validation, analytics, a11y, copy, tests.
**Done when:** every in-scope M4 row `DONE` or `NOT_NEEDED` with a matrix citation.

### M5 Backend gaps
Implement `API_GAP_LIST.md` on the existing backend: pagination/filters, push tokens, notification hooks, idempotency, rate limits, AI quotas, audit (device + app version), consent on customer capture. Load `push-notifications` for the token and delivery contract. Migrations with rollback. Reuse web logic.
**Done when:** every gap `DONE` or `BLOCKED`.

### M6 Security
Load `masvs-checklist`, then `secure-storage-audit`, `auth-assessment`, `network-security-check`, and `secrets-scan`. Walk MASVS groups STORAGE / CRYPTO / AUTH / NETWORK / PLATFORM / CODE / RESILIENCE / PRIVACY. Write `SECURITY_REPORT.md`.
**Done when:** M6.1 `DONE`.

### M7 Tests
Load `react-native-testing` and `maestro-mobile-testing`. Jest + RNTL + Maestro. Unit, component, integration (test DB), authz per role, offline replay, e2e demo on iOS and Android, web↔mobile parity, edge cases (0812 / +62812 / 62812, duplicate IDs, last-unit race, limit exact/over, weak net, kill mid-sync, expired token, logged-out deep link, time zones). Synthetic data only.
**Done when:** M7.1–M7.4 `DONE`. Unrun tests = `UNVERIFIED`, not `DONE`. QC rows in `QUALITY.md` cite those runs.

### M8 Performance
Load `management` for the tool order. Measure with `react-native-best-practices`, then `performance-optimization` only for a failed budget. Load `sentry-react-native` and `amplitude-expo`. Keys stay in EAS env. Mid-range Android + iPhone.
**Done when:** M8.1–M8.3 `DONE`.

### M9 Release
Load `release-management`, then eas-app-stores, eas-update, eas-workflows, app-icon; local-build if needed. `RELEASE = GO` is required. Production profiles, listings, privacy, OTA, force-update, staged rollout, rollback, TestFlight/internal checklist.
**Done when:** M9.1–M9.3 `DONE`.

### M10 Demo + handover
Load `documentation`. Seed 3 stores, 2 customers, 1 competitor-filled slot. Demo script must run cleanly 3 times from a fresh DB, phone and web side by side. README, architecture, API usage, env setup, release, runbook, final summary (verified / UNVERIFIED / risks).
**Done when:** M10.1–M10.4 `DONE`. Load `quality`. Q0–Q3 are `DONE` or `BLOCKED`. `RELEASE` is set. `HOLD` means the track is not done.

## SCREEN DONE CHECK
Intentional and on-system; every state designed; one-handed at a bright counter and in dark mode; copy actionable; AA + font scale + screen reader + reduced motion; 60fps; no layout jump; skeletons over spinners; primary action obvious in two seconds.

## FINAL DELIVERABLES
**Track S:** `DNA_LEDGER.md`, `STUDIO_BRIEF.md`, `SHOWCASE.md`, `QUALITY.md` (QM, QA, QC, QI, `RELEASE`), design system, full screen set with states, prototype or code, rubric ≥85.
**Track P / BOTH:** plus the production set below.
1. Working iOS + Android app on the real backend; demo scenario passing.
2. `docs/` M0 six files.
3. `docs/` M1 four files + `DESIGN_SYSTEM.md`.
4. `ARCHITECTURE.md`, `SECURITY_REPORT.md`, `TEST_REPORT.md`, `PERFORMANCE_REPORT.md`.
5. `ASSUMPTIONS.md`, `OPEN_QUESTIONS.md`, `BLOCKERS.md`, `PROGRESS.md`, `QUALITY.md`.
6. Final summary in the agent's last message and in `docs/HANDOVER.md`.

## START
Execute §0 now, including the track pick. Track S → design-studio phases 0–9. Track P → M0. Track BOTH → studio 0–6 then M0. Do not wait.
