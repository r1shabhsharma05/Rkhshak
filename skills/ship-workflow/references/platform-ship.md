# Platform Ship — Chrome extensions and Expo apps

Distilled from two sources, in our own words: chrome-extensions (MIT) and its `extensions/` and `webstore/` references, and expo-pro (MIT). Full detail lives in those sources. Use when building or publishing a Chrome extension, or shipping a cross-platform mobile app with Expo.

## Chrome extensions (Manifest V3, always)
- **Mandatory rules (the ones that bite):** reference only icon files you created (or omit icons); a side panel must have a way to open it; code execution only in sandboxed iframes; `tab.url` needs the `tabs` permission; always `async`/`await`, never `.then()` chains; do not block the main thread from content scripts; service workers are ephemeral — never store state in variables; the extension ID differs between dev and production (identity flows must handle both); `activeTab` works only on direct user gestures, not from side panels; `chrome.permissions.request()` in a service worker must be called with no `await` before it in the message listener; offscreen documents have no access to most `chrome.*` APIs; notifications and badge icons must reference real image files; `chrome.windows` has no `.query()` — use `getAll`, `getLastFocused`, or `getCurrent`.
- **Structure:** manifest, service worker, popup/side-panel UI, content scripts, message passing between them, storage, permissions declared minimally (each permission earns its place).
- **Publishing to the Chrome Web Store:** keep a store-listing document (description, screenshots, privacy policy, review checklist) beside the code; fill it from the actual extension, not from aspiration; run the pre-publish checklist (permissions justified, privacy policy present, listing copy honest) before submitting.

## Expo apps (managed React Native)
- **Mental model:** write JS/TS → EAS builds native binaries in the cloud → EAS Update ships JS changes instantly. Native changes still need a new build.
- **Expo Router:** file-based routing (layouts, tabs, stacks, deep linking by file structure); typed routes reduce navigation bugs.
- **EAS Build:** cloud builds producing installable binaries from `eas.json` profiles (development, preview, production). No Mac required for iOS builds.
- **EAS Update:** over-the-air updates for JS and assets — publish, and users get it on next launch.
- **Config plugins:** JS functions that patch native projects at prebuild time (permissions, entitlements, manifest keys). Prefer plugins over manual native edits — manual edits are wiped on prebuild.
- **Development builds:** a custom dev client replacing the generic one when custom native modules are used.
- **Identity early:** bundle IDs, app names, icons, splash, and permissions are set in config before the first production build — changing identity late is expensive.
- **SDK alignment:** SDK modules are versioned together per release; keep them aligned, and eject to the bare workflow only when config plugins cannot cover a native need.
