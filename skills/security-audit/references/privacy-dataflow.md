# Privacy Data-Flow — where personal data goes, and how it leaves

Compliance mapping says which law applies. This is the practical version: trace every piece of personal data through the system, and prove it can be deleted.

## The map (build it first)
For every kind of personal data the app holds, write one row:
| Data | Collected where | Stored where | Who can read it | Shared with whom | Kept how long | Deleted how |
|---|---|---|---|---|---|---|
| Name, email | Signup form | users table | The user, admins | Nobody | Until account deleted | Delete-account flow |
| Phone | OTP verification | users table | The user | SMS provider | Until account deleted | Delete-account flow |
| Location | SOS alert | sos_alerts table | Guardians, user | Nobody | 90 days | Scheduled purge |
| Payment | Checkout | Payment provider (not us) | — | Stripe/Razorpay | Per provider | Via provider |

If a row has a blank cell, that's a finding — the team doesn't know where the data goes.

## Rules
### 1. Collect the minimum
- Every field collected must have a named reason (the feature that needs it). A field with no reason is deleted from the form and the database.
- Never collect data "for later". Later is not a reason.

### 2. Purpose limitation
- Data is used for the purpose it was collected for, and nothing else. An email collected for login is not used for marketing unless the user opted in.
- Analytics does not carry PII. If an analytics event contains an email, a name, or a user id that identifies a person, it's a leak.

### 3. Access control on data
- Who can read each table is written down and enforced (RLS / server-side checks). An admin who can read everything is a finding unless the design demands it.
- Support/debugging access is logged. If someone reads a user's data, there's a record.

### 4. Third parties are in the map
- Every third party that receives personal data is listed: name, what data, why, where their privacy policy is, whether there's a data-processing agreement.
- A third party not in the map but receiving data is a finding.

### 5. Retention + deletion
- Every table has a retention period. Old data is purged on a schedule, not kept forever.
- Delete-account actually deletes: the user's rows, their files, their data in third parties (or the request is sent). A "delete" that only hides the account is not a deletion.
- Backups: deleted data disappears from backups on the backup retention cycle. Say how long that takes — don't pretend it's instant.

### 6. Consent is real
- Consent is opt-in, specific, and revocable. A pre-ticked box is not consent. Withdrawing consent actually stops the processing.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Data-flow map exists, no blank cells | A data type with unknown storage, access, or retention |
| 2 | Every field has a named reason | A field collected with no reason |
| 3 | Analytics carries no PII | An email/name/user id in an analytics event |
| 4 | Third parties all listed with data + purpose | A vendor receiving data but not in the map |
| 5 | Retention periods set + purge runs | Data kept forever, no purge |
| 6 | Delete-account deletes (rows, files, third parties) | A "delete" that only hides the account |
| 7 | Consent opt-in, specific, revocable | Pre-ticked boxes, or withdrawal doesn't stop processing |

## How this maps to the 85 checks
Privacy/legal (Area 12) and compliance-mapping are the 85-check homes. This reference is the working map — the table that proves the team knows where personal data lives and how it leaves.
