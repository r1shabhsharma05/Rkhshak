# Container Security — Docker images that don't leak the host

A container is not a sandbox by default. An image built carelessly hands an attacker the app, its secrets, and a path to the host. Audit the image, not just the code inside it.

## Rules
### 1. Minimal base image
- Use a minimal base (distroless, alpine, slim) — fewer packages, fewer vulnerabilities. A full OS image in production is a finding.
- Pin the base image by digest, not by a moving tag (`node:20` moves; a digest doesn't). Rebuild on a schedule so patches land.

### 2. Scan before deploy
- Scan every image before it ships (Trivy, Grype, Docker Scout). A Critical or High with a fix available blocks the deploy until fixed or risk-accepted in writing.
- Scan the final image, not just the build stage. Multi-stage builds: the runtime stage carries only what the app needs.

### 3. Run as non-root
- The container runs as a non-root user (`USER 1000` or a named user). Root in a container that escapes is root on the host.
- No `--privileged`, no Docker socket mounted into the container, no host network unless the design demands it (and then it's documented).

### 4. No secrets in the image
- No secret in a Dockerfile layer (a secret in any layer stays in the image history even if a later layer deletes it). Secrets arrive at runtime via env vars or a secrets manager, never baked in.
- No `.env`, no private key, no credential file copied into the image. Check with a scan of the final image.

### 5. Read-only + minimal capabilities
- Filesystem read-only where possible (`--read-only`), with only the directories the app must write mounted as volumes.
- Drop unneeded Linux capabilities (`--cap-drop=ALL`, add back only what's needed). The container gets the minimum power to do its job.

### 6. Resource limits
- CPU and memory limits set. A container with no limit is a denial-of-service waiting to happen (one runaway process takes the host).

### 7. Keep it updated
- Base images and dependencies rebuilt on a schedule (weekly at minimum). An image that hasn't been rebuilt in 6 months is carrying 6 months of vulnerabilities.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Minimal base image, pinned by digest | Full OS image, or a moving tag |
| 2 | Image scanned before deploy, no unfixed Critical/High | Unscanned image, or known vulns shipped |
| 3 | Runs as non-root | Container runs as root |
| 4 | No secrets in any image layer | A key, token, or `.env` in the image |
| 5 | No `--privileged`, no Docker socket, no host network | Any of the three present without a documented reason |
| 6 | Read-only filesystem + dropped capabilities | Writable root FS with full capabilities |
| 7 | CPU/memory limits set | No limits |
| 8 | Image rebuilt on a schedule | Last build over a month old with no rebuild |

## How this maps to the 85 checks
Deployment/config (Area 10) is the 85-check home. This reference is the container version — the image, the runtime flags, and the rebuild discipline.
