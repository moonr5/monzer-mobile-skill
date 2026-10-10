---
name: maps-location
description: Add a map and device location to an Expo app for field staff, store finding, or a route the existing system already has. Use when a screen must show places or the user's position.
---

# Maps and location

Load this only when the scope matrix has a map, a store finder, or a field visit. Skip it for a counter-only app.

## Setup

1. Inspect the SDK. `npx expo install expo-location`. Add `react-native-maps` only when the screen draws a map. A list of addresses does not need a map.
2. A map needs a dev client or a store build, plus the provider key (Google or Apple) in EAS secrets. The key is not committed and not shipped in a public bundle if the provider allows a restricted key.
3. Ask for location when the user opens the map. The prompt says why. Foreground is the default. Background location only if the existing product already tracks staff between visits, and the purpose string says so.
4. Denied permission still shows the places from the API. The user can search or pick from a list.
5. Markers and the selected place come from the existing backend. Tapping a marker opens the existing store or visit screen.
6. Do not send precise coordinates to analytics. If a visit must be recorded, send it to the existing API as that product already does on the web.
7. Cover loading, empty (no places), error, offline, and permission denied. The map does not replace the list.

## Done

The places on the phone match the web data. A denied permission still lets the user finish the task. Evidence in `TEST_REPORT.md`, or `UNVERIFIED`.
