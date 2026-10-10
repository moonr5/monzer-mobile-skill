---
name: camera-scan
description: Add a camera preview and barcode scan overlay to an Expo app. Use for product scan, QR, shelf labels, or any screen that must read a code into the existing system.
---

# Camera and scan

Use this only when a screen in `SCREEN_INVENTORY.md` scans a code or takes a photo. Inspect the Expo SDK, then `npx expo install expo-camera`.

## Setup

1. Add the `expo-camera` config plugin. The permission string says what is being scanned, in the product's language.
2. Enable barcode scanning only when the screen reads codes. Leave the microphone off unless the screen records video.
3. Request camera permission when the user opens the scanner, not at launch. Denied and restricted are designed states with a way to open settings.
4. The overlay comes from the design system: viewfinder, torch, cancel, and the last result. Status is never color-only.
5. Debounce. The same code in a short window produces one action. A scan calls the existing API (product, slot, order). It does not create a second catalog.
6. Handle no-camera, permission denied, unreadable code, code not in the system, and a weak network. The success state names what was found and the next action.
7. Do not store the camera frame. Store the code and the server result.
8. A scan works one-handed at a bright counter. Torch is available. The primary action stays reachable.

## Done

On a device, a known code resolves through the real API and an unknown code shows the error state. Evidence in `TEST_REPORT.md`, or `UNVERIFIED`.
