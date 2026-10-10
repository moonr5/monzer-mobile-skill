---
name: i18n-rtl
description: Add languages, locale formats, and right-to-left layout to an Expo app. Use when copy, dates, currency, or layout direction must follow the device or the existing product language.
---

# Language and RTL

Also read `skills/mobile-design/references/adaptivity-localization.md`. On Track P the existing product's language wins. Do not invent a second catalog of strings.

## Setup

1. If the app already has an i18n library, extend it. If it does not, add one and `npx expo install expo-localization`. Pick one library and record it in `ARCHITECTURE.md`.
2. Detect the device language. A settings control can override it. Persist the override. Fall back to the product's default language. Use Indonesian only when the system market is Indonesian.
3. New screens have no hardcoded user-facing strings. A missing key fails the build or renders the key in development, never a blank label.
4. Dates, numbers, and currency use the locale from `expo-localization` or the account's region. Do not hardcode `$` or `MM/DD`.
5. RTL only when a shipped language has `textDirection: rtl`. Allow RTL. Do not force it for an LTR-only product. `forceRTL` needs a reload before layout changes.
6. New layout uses start and end, not left and right. Icons that point along the reading direction flip. Icons that depict an object do not.
7. Check a long string and a short string. Truncation is a defect when it hides the action.
8. Language files live next to the feature. The web app's existing translations are the source when they exist.

## Done

Switching language changes the visible copy and the formats. An RTL language, if in scope, mirrors the layout after reload. Evidence in `TEST_REPORT.md`, or `UNVERIFIED`.
