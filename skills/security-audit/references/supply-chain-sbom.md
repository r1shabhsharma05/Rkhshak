# Supply-Chain Security + SBOM

Most vulnerabilities in a modern app do not come from code the team wrote. They come from dependencies — packages, actions, images, and the tools that build them. Audit the chain, not just the code.

## Rules

### 1. Lockfile is law
- The lockfile is committed, and installs use it (`npm ci`, not `npm install`). A build that resolves "latest" at install time is not reproducible and not auditable.
- Any change to the lockfile is reviewed like a code change: what was added, what was removed, what version moved.

### 2. Audit every dependency
- Run a dependency audit on every PR and before every release: `npm audit`, OSV, GitHub Advisory Database, or the repo's own audit workflow. A known Critical or High with a fix available is a FAIL until it is fixed or risk-accepted in writing.
- Count the findings, don't just list them. A project with 500 dependencies and 0 findings is different from one with 15 findings nobody looked at.

### 3. Vet before adding
- Before a new dependency is added: is it maintained (recent commits, open issues answered), does it have a sane size, does it do something the stdlib or an existing dependency already does? If yes to the last one, don't add it.
- Check what the package actually runs at install time (install scripts, postinstall hooks). A package that runs arbitrary code on install is a supply-chain risk until reviewed.

### 4. SBOM — know what's inside
- Generate a Software Bill of Materials for every release: every component, its version, its license, its source. Formats: CycloneDX or SPDX.
- The SBOM is stored with the release, not generated on demand and forgotten. When a new CVE drops, the SBOM answers "are we affected?" in minutes, not days.

### 5. Provenance — prove where it came from
- Packages are published with provenance (signed, built by CI, linked to a source commit). Prefer packages with npm provenance or SLSA attestations.
- Never install a package from an unverified URL, a random tarball, or a command that pipes a script into a shell (`curl | sh`) without reading it first.

### 6. Pin and monitor
- Pin versions in production. Ranges (`^`, `~`) are fine in development; the lockfile is what pins the release.
- Monitor continuously: Dependabot, Renovate, or a scheduled audit. A dependency that was safe at release time can become vulnerable the next day.

### 7. Actions and images too
- CI actions are pinned to a full commit SHA, not a moving tag (`@v4` moves; a SHA does not).
- Container base images are pinned by digest, scanned before deploy, and rebuilt on a schedule — not left running a six-month-old image.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Lockfile committed, installs use it | Builds resolve "latest" at install time |
| 2 | Dependency audit clean (or risk-accepted in writing) | Known Critical/High unfixed and unrecorded |
| 3 | New dependencies vetted (maintained, needed, install scripts reviewed) | A package was added without review |
| 4 | SBOM generated per release (CycloneDX or SPDX) | No SBOM, or it doesn't match the release |
| 5 | Packages have provenance / signed | Installed from unverified URLs or `curl \| sh` |
| 6 | Continuous monitoring enabled (Dependabot / Renovate / scheduled audit) | No monitoring; vulnerabilities found by accident |
| 7 | CI actions pinned to SHA, images pinned by digest + scanned | Moving tags or unscanned images in the pipeline |

## How this maps to the 85 checks
Dependencies (Area 9) is the 85-check home for this. This reference is the deep version: lockfile discipline, SBOM, provenance, and CI/image hygiene.
