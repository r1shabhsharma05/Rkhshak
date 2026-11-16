# Cloud Misconfiguration

Most cloud breaches are not clever exploits. They are a public bucket, an open database, or a key that should have been deleted. Audit the configuration, not just the code.

## Rules

### 1. Nothing public by accident
- Storage buckets (S3, GCS, Blob): private by default. Public access is blocked at the account level, and any public bucket is listed by name with the reason it must be public.
- Databases: never reachable from the internet unless the design demands it — and then behind IP allowlisting or private networking, never `0.0.0.0/0`.
- Admin consoles (cloud dashboard, database dashboard): MFA on, no shared root credentials, no access keys lying in a repo.

### 2. IAM — least privilege, always
- Every role, user, and service account gets the minimum permissions its job needs. `*` permissions are a finding until justified.
- No long-lived access keys for humans — SSO / short-lived credentials instead. Unused keys and roles are deleted, not left "just in case".
- Separate accounts/roles per environment: dev cannot touch prod.

### 3. Secrets live in a secrets manager
- No secret in code, config files, env files committed to git, or chat. Secrets live in the cloud secrets manager (or the platform's env store) and are referenced by name.
- Rotation: every secret has an owner and a rotation plan. A secret that has never rotated is a finding.

### 4. Encryption everywhere
- At rest: storage, databases, backups encrypted. At transit: TLS, no cleartext endpoints.
- Keys managed by the cloud KMS, not hardcoded, not in the repo.

### 5. Logging and alerts on
- Audit logs enabled for every service (CloudTrail / Audit Logs / Activity Log), retained, and monitored. An alert fires on: root login, IAM change, public bucket change, failed auth spikes.
- If nobody looks at the logs, they don't exist. Name the person or the alert that watches them.

### 6. Network boundaries
- Security groups / firewall rules: only the ports the service needs, only from the sources it needs. `0.0.0.0/0` on a database or SSH port is a Critical finding.
- Private subnets for databases and internal services; only the load balancer / edge is public.

### 7. Backups and recovery
- Automated backups on, retention set, restore tested (a backup that has never been restored is a hope, not a backup).
- Backups are encrypted and access-controlled like the data they hold.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | No public storage bucket without a named reason | A bucket is public and nobody knows why |
| 2 | No database reachable from the internet (or allowlisted) | DB open to `0.0.0.0/0` |
| 3 | IAM is least-privilege; no `*` without justification | Wildcard permissions, unused roles/keys |
| 4 | Secrets in a secrets manager, rotation planned | A secret in code, config, or chat |
| 5 | Encryption at rest + in transit everywhere | Unencrypted storage or a cleartext endpoint |
| 6 | Audit logs on, retained, alerted | Logging off, or no one watches it |
| 7 | Security groups minimal; DB/SSH not open to the world | `0.0.0.0/0` on a sensitive port |
| 8 | Backups on + restore tested | No backups, or never restore-tested |

## How this maps to the 85 checks
Deployment/config (Area 10) and Database/storage (Area 4) are the 85-check homes. This reference is the cloud-console version — the settings the code cannot see.
