# Compliance Mapping — 85 checks to GDPR / DPDP / SOC 2 / PCI-DSS

The 85-check audit is a security audit, not a compliance certification. This file maps the checks to the major frameworks, so a user who needs compliance can see which checks cover which requirement — and which requirements need more than the audit.

## How to use it
- Find the framework(s) that apply to the product. Read the mapped checks. If a mapped check fails, that framework requirement is not met.
- **A passing audit does not mean compliant.** Compliance also needs policies, processes, contracts, and records that code alone can't prove. This mapping shows coverage, not certification.

## GDPR (EU) — key requirements
| Requirement | 85-check | Notes |
|---|---|---|
| Lawful basis + consent | 12.2 | Tracking waits for consent; consent is recorded. |
| Data minimization | H6 | Don't store what you don't need. |
| Right to erasure | 12.3 | Deletion removes data from DB, storage, and connected tools. |
| Breach notification (72h) | incident-response.md | Notify the regulator within 72 hours of becoming aware. |
| Privacy by design | 4.3, 4.5 | Private by default, RLS on, least privilege. |
| Data protection impact assessment | threat-model.md | Run a threat model for high-risk processing. |

## DPDP Act (India) — key requirements
| Requirement | 85-check | Notes |
|---|---|---|
| Consent (verifiable, withdrawable) | 12.2 | Consent is specific and can be withdrawn. |
| Children's data (verifiable parental consent) | H15 | Age check; parental consent as the rules phase in. |
| Data principal rights (access, correction, erasure) | 12.3 | Users can access, correct, and delete their data. |
| Breach notification | incident-response.md | Notify the Data Protection Board and affected users. |
| Data retention limits | H6, 12.1 | State how long data is kept (privacy policy). |

## SOC 2 (Trust Services Criteria) — key areas
| Criteria | 85-check | Notes |
|---|---|---|
| Security (CC6, CC7) | Areas 1–6, 9–10 | Access control, encryption, monitoring, change management. |
| Availability (A1) | H14, 11.2 | Uptime monitor, no runaway costs, backups. |
| Confidentiality (C1) | 1.1–1.4, 4.3, 4.5 | Secrets, private storage, RLS. |
| Processing integrity (PI1) | 5.1, 5.6, 7.1–7.3 | Input validation, safe errors, correct payment handling. |
| Privacy (P1–P8) | Area 12 | Privacy policy, consent, erasure, retention. |

## PCI-DSS (if the product handles card data) — key requirements
| Requirement | 85-check | Notes |
|---|---|---|
| Don't store card data | H6 | Never store card numbers. Use the payment provider's tokenization. |
| Protect stored data | 4.1, 4.3 | If any payment data is stored, it is encrypted and access-controlled. |
| Secure transmission | 13.2, 6.2 | HTTPS everywhere, no cleartext. |
| Access control | Area 3 | Least privilege, admin protected server-side. |
| Test + monitor | 9.1, 10.5, H14 | Dependency audit, logging, uptime/error monitoring. |
| **Best practice:** use a payment provider (Stripe/Razorpay) and never touch card data directly — then PCI scope is minimal (SAQ-A). | 7.1–7.6 | Prices server-side, access only after verified payment. |

## What the audit does NOT cover (needs a human / lawyer)
- Whether the privacy policy's wording is legally sufficient.
- Whether contracts with processors (DPA) are in place.
- Whether the lawful basis chosen is correct for the processing.
- Certification, attestation, or a formal audit report.
- Jurisdiction-specific rules beyond the ones listed here.
