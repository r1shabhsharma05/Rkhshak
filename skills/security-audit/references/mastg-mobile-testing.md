# OWASP MASTG — Mobile App Security Testing

The OWASP Mobile Application Security Testing Guide (MASTG) is the standard for testing a mobile app's security. This reference maps it onto the audit so a mobile app is tested, not just reviewed.

## What MASTG is
- **MASVS** (Mobile Application Security Verification Standard): what "secure" means for a mobile app — 8 categories, 3 assurance levels (L1 standard, L2 defense-in-depth, R resilience against reverse engineering).
- **MASTG**: how to test each MASVS requirement — static analysis, dynamic analysis, and manual checks.

## The 8 MASVS categories (test each one)
| Category | What to test |
|---|---|
| Storage | Sensitive data at rest: Keychain/Keystore (not plain files, not SharedPreferences/UserDefaults), no secrets in logs, no sensitive data in screenshots or the app switcher, backup flags off (`allowBackup=false`, `android:debuggable=false`). |
| Crypto | Real crypto, not home-made: platform APIs, no hardcoded keys, no weak algorithms (MD5, SHA1 for passwords, DES), random IVs, keys in the keystore. |
| Auth | Session handling, token storage (secure storage, not plain text), biometric auth is a convenience not a replacement for server auth, logout actually invalidates the token server-side. |
| Network | TLS everywhere, certificate pinning (and a plan for when the cert rotates), no sensitive data in URLs, no cleartext traffic (`usesCleartextTraffic=false`, ATS on). |
| Platform | Deep links validated (no unauthenticated deep link reaching a protected screen), IPC (intents, URL schemes) guarded, WebView locked down (no JS bridge to native unless needed, no file access). |
| Code | No secrets in the binary (strings scan), no debug code in release, obfuscation on for release builds, no sensitive logic that only the client enforces. |
| Resilience | (L2/R) Root/jailbreak detection, tamper detection, anti-debugging, emulator detection — and a decision about what happens when detection fires (block, warn, or log). |
| Privacy | Data collected is declared, permissions requested are the minimum, third-party SDKs listed, analytics does not leak PII. |

## How to test
1. **Static:** decompile the APK/IPA (or read the bundle). Grep for secrets, check the manifest/plist, list permissions, inspect the lockfile. No device needed.
2. **Dynamic:** run the app on a device/emulator with a proxy (Burp/mitmproxy). Watch every request: TLS? pinning? tokens in URLs? sensitive data in responses?
3. **Manual:** try the attacks — log out and replay the token, deep-link into a protected screen, background the app and screenshot it, read the app's files from a rooted device.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Secrets stored in Keychain/Keystore only | Tokens or keys in plain files, logs, or the binary |
| 2 | TLS everywhere + pinning (with a rotation plan) | Cleartext traffic or no pinning on sensitive calls |
| 3 | Logout invalidates the token server-side | Old token still works after logout |
| 4 | Deep links / intents validated | Unauthenticated deep link reaches a protected screen |
| 5 | Release build: no debug, obfuscated, backup off | Debuggable release or data extractable via backup |
| 6 | Root/jailbreak + tamper detection present (L2/R) | No detection on a high-value app |
| 7 | Permissions are the minimum the app needs | Location/contacts/camera requested without a feature using them |
| 8 | MASVS level declared (L1/L2/R) and met | No level declared, or L1 requirements failing |

## How this maps to the 85 checks
Mobile/Expo (Area 13) is the 85-check home. `references/mobile-security.md` is the checklist version. This is the testing method — how to prove each mobile check with static, dynamic, and manual evidence.
