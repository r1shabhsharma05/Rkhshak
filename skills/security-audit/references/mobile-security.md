# Mobile Security Deep-Dive — beyond the 7 Expo checks

Area 13 of the 85-check audit covers the basics (secure token storage, HTTPS, deep links, WebViews, permissions, account deletion, clean release build). This file goes deeper. Run it on every mobile app.

## Storage
- Tokens use the platform secure store (iOS Keychain, Android Keystore via `expo-secure-store`) — never AsyncStorage, plain files, or SharedPreferences.
- Sensitive data (health, financial, private messages) is encrypted at rest, not just "in the app's sandbox".
- No secrets in the app bundle (no API keys, no JWT secrets, no service keys in the binary — they can be extracted).
- Clipboard: sensitive values (codes, passwords, tokens) are never copied to the clipboard automatically, and are cleared after use.
- Screenshots/screen recording: sensitive screens (payment, OTP, private data) block screenshots where the platform allows it (`FLAG_SECURE` on Android, screen-capture blocking on iOS).

## Network
- All traffic is HTTPS. Certificate pinning is used for the app's own API (so a proxy with a trusted cert can't intercept). Pinning has a fallback/rotation plan so a cert rotation doesn't brick the app.
- No cleartext traffic (Android `cleartextTrafficPermitted=false`, iOS App Transport Security with no broad exceptions).
- API responses are validated (never trusted blindly). Timeouts and retries are bounded (no infinite retry loop burning battery/data).

## Authentication
- Biometric auth (Face ID / fingerprint) is offered where it fits, and it gates the sensitive action — not just the app launch. Biometric failure falls back to the device passcode, never to "skip".
- Session tokens expire and refresh securely (refresh token is stored in the secure store, rotated on use, revoked on logout).
- Logout actually ends the session (token revoked server-side, not just deleted locally).

## Platform
- **Root/jailbreak detection:** the app detects rooted/jailbroken devices and either warns the user or refuses sensitive actions (payments, private data). It never silently trusts a compromised device.
- **Tamper detection:** the app detects repackaging/modification where the platform supports it (Play Integrity on Android, DeviceCheck/App Attest on iOS).
- **Permissions:** minimal, requested when needed, with a clear reason. The app works (degraded, not broken) when a permission is denied.
- **Deep links:** validated (parameters checked, never trigger payments/account changes/deletions without login + confirmation). Universal links / App Links are used (not just custom schemes, which any app can claim).
- **Push notifications:** never contain codes or private data. Tapping a notification requires login for sensitive content.

## Release
- Debug menus, test screens, verbose logs, and test endpoints are off in the store build.
- The app binary is not debuggable in release (`debuggable=false` on Android, no debug symbols shipped).
- ProGuard/R8 (Android) or equivalent obfuscation is on for release builds.
- App Store privacy labels and Google Play Data safety form match what the app really collects (H17).
- Force-update works: the app can require an update when a security fix ships (H18).
