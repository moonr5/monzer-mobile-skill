---
name: push-notifications
description: Add push and local notifications to an Expo client of an existing system. Use for permission, device tokens, Android channels, tap-to-open, and server delivery. Remote push is sent by the existing backend.
---

# Push notifications

Inspect the Expo SDK, the existing notification tables, and `API_GAP_LIST.md` before adding a package. Remote push is a feature of the existing backend. The app only registers a device token and opens the right screen.

## When

Load this for M4 notifications and M5 push-token gaps. If the scope matrix marks notifications `WEB_ONLY` or `NOT_NEEDED`, stop and record that.

## Setup

1. `npx expo install expo-notifications expo-device` after you know the SDK from `package.json`.
2. Remote push needs a physical device and a development or production build. Confirm the current SDK docs before assuming Expo Go can receive a remote push.
3. Add the config plugin only if the installed `expo-notifications` version requires it. Permission strings say why this product needs alerts, in the product's language.
4. Android: create the channel before requesting a token.
5. Read the current permission. Ask at a moment that makes sense (the user turned alerts on, or finished the first real task). A denial is a screen state, not a crash.
6. Resolve the EAS project id from the current Expo config. Request the Expo push token. Upsert it on the existing backend with user, device, platform, and last-seen. Listen for token refresh when that SDK supports it.
7. Never send a push from the app. The existing backend calls the Expo push API. Batch within the current limits. Read tickets, then receipts. Disable a token only on an authoritative `DeviceNotRegistered`. Retry transient failures. Do not retry a malformed payload.
8. A tap opens an existing deep link. Handle foreground, background, and cold start. Logged-out taps go to sign-in, then to the destination.
9. Badge count matches the server's unread count. Clearing a notification on one client clears it on web.
10. FCM and APNs keys stay in EAS secrets or the Expo dashboard. `google-services.json` is not committed. Record every env name in `ARCHITECTURE.md`.

## Done

A test push to a registered device arrives, the tap opens the right screen, and a dead token is removed. Evidence is a command or a device note in `TEST_REPORT.md`. Unrun = `UNVERIFIED`.
