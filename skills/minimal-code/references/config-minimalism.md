# Config Minimalism — sane defaults, fewest options

Every config option is a second code path to test, document, and maintain. The fewest options that solve the problem is the right number — with sane defaults doing the rest.

## The rules
- **Sane defaults first.** The app works well with zero configuration. A user who never touches a setting gets the right behaviour. Configuration is for the exception, not the rule.
- **One value = hardcode it.** A config file, an env var, or a settings screen for a value that has exactly one value today is not configuration — it's indirection. Hardcode it. When the second value arrives, then make it configurable. (See `references/yagni.md`.)
- **Every option must have a user.** An option nobody asked for is deleted. "Someone might want it" is not a user.
- **Fewer options, better names.** Three options named clearly beat ten options named vaguely. An option named `advancedMode` says nothing — what does it advance?
- **Config lives in one place.** One config file (or one env scheme), documented, with every option's default + what it changes. Config scattered across five files is a finding.
- **No config for what the code can decide.** If the app can detect it (screen size, language, timezone), detect it. Don't ask the user to configure what the app already knows.
- **Env vars are for secrets + environment, not for features.** A feature flag is fine (temporary, with an expiry). A dozen env vars that change behaviour is a second app hiding in the config.

## The cost of an option
- **Testing.** Every option doubles the behaviour to test. Three boolean options = eight combinations. Most of them never get tested.
- **Documentation.** Every option needs explaining. Ten options need a page; three need a line.
- **Support.** Every option is a question ("what does this do?") and a way to break the app ("I changed this and now it doesn't work").
- **Decision fatigue.** A user facing ten settings before they can start will not start.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | App works well with zero configuration | Requires setup before first use |
| 2 | No config for a single value | An env var / setting for one value |
| 3 | Every option has a named user who asked for it | An option "someone might want" |
| 4 | Config lives in one place, documented | Config scattered across five files |
| 5 | App detects what it can (no config for detectable things) | A setting for screen size or timezone |
| 6 | Feature flags are temporary, with an expiry | A flag that's been there for a year |
