# Email checks — verdicts, and the SMTP limit stated honestly

Distilled from `check-if-email-exists` (MIT, reacherhq/check-if-email-exists)
and `render_free_email_delivery` (SMTP-blocked → provider HTTP API).
Own words; local install paths are not carried over.

## What a check can say
Verify an address exists **without sending any mail**: syntax, disposable
provider, typo suggestion, role account, and MX records. Verdicts:
`invalid` | `typo` | `role-account` | `disposable` | `domain-ok`.
- `invalid` — bad syntax, or the domain does not exist. Drop it.
- `typo` — a lookalike domain of a major provider (e.g. gmali.com). Fix the
  typo; never send to the typo'd address.
- `role-account` — info@/admin@/support@ and the like. Do not cold-email it.
- `disposable` — a throwaway domain. Drop it.
- `domain-ok` — the domain accepts mail. **That is all it means.**

## The honest limit (read before trusting any output)
- **`domain-ok` does NOT mean the mailbox exists.** It means the domain
  accepts mail. Mailbox existence is the SMTP check, and SMTP deliverability
  checks are often impossible from a sandboxed host: outbound port 25 is
  commonly blocked at egress, and a forwarding proxy is not a SOCKS proxy.
  Never report an address as verified-deliverable from this tool alone.
- A mailbox check that cannot connect reads `unknown` on the SMTP part —
  unknown is not "deliverable", it is unproven.
- Gmail/Workspace addresses deserve extra caution: Gmail does not confirm
  deliverability over SMTP the way other providers do. Treat a Gmail verdict
  with the same caution as any other `domain-ok`.
- Some verifier builds have dead fields (e.g. disposable/role flags that
  always read false). Do not read a field the tool's own checks show is dead;
  decide disposable/role from the address itself and a maintained list.
- A syntax gate can also reject disposable domains and typo domains — split
  syntax, disposable, and typo apart before reporting a verdict.

## How to use it (pre-filter, not a verdict)
1. Run the check on each guessed address first: drop `invalid` /
   `disposable` / `typo` (fix the typo), skip `role-account` for cold email,
   and send only `domain-ok` addresses on to a deliverability check.
2. It is a pre-filter, not a replacement for deliverability verification.
3. Never bulk-verify harvested lists for spam. Verification is only for
   addresses already inside an approved outreach flow.

## When mail itself will not send (blocked SMTP → provider HTTP API)
- **Recognise the pattern.** A connection timeout on port 587/465 from a
  free-tier host is the platform blocking outbound SMTP. Stop debugging SMTP
  at that point — switching ports, credentials, or mailer settings returns
  the same timeout. An authentication error, by contrast, is a credential
  problem: fix only the credential.
- **Switch to the provider's HTTPS API.** Use the HTTP API of the mail
  provider already in use (e.g. the provider's REST send endpoint) and keep
  the provider the user already chose. The API key comes from the user
  through the secure flow and lives as an environment variable on the host —
  never in a skill, a memory file, or a repository file. Remove SMTP
  host/port/password variables the app no longer reads. Replace only the mail
  sending path.
- **Verify the send end to end.** Send one test message through the provider
  API, record the provider response status and message id, confirm it arrived
  in the recipient mailbox (ask the user to confirm receipt when that mailbox
  cannot be read directly), then run the real flow (signup, password reset)
  against the live deployment and check the service logs. Report the test send
  and the live-flow result together, naming the provider and API route used.
