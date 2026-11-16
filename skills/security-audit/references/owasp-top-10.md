# OWASP Top 10 (2025) + LLM Top 10 (2025) — mapped to the 85 checks

Run alongside `pre-launch-audit-85-rules.md`. Each OWASP item maps to one or more 85-check areas. A check passes only on evidence, same as the 85 rules.

## OWASP Top 10 for Web (2025)
| # | Risk | Maps to 85-check |
|---|---|---|
| A01 | Broken Access Control | 3.1–3.6, 4.5 |
| A02 | Security Misconfiguration | 10.1–10.5, 13.7 |
| A03 | Software Supply Chain Failures | 9.1–9.4 |
| A04 | Cryptographic Failures | 2.2, 2.5, 4.3, 13.1 |
| A05 | Injection | 4.1, 5.1 |
| A06 | Insecure Design | 2.3, 3.2, 3.4, 7.1–7.6 |
| A07 | Authentication Failures | 2.1–2.7, 6.1 |
| A08 | Software or Data Integrity Failures | 9.2–9.4, 6.6 |
| A09 | Security Logging & Monitoring Failures | 10.5 |
| A10 | Server-Side Request Forgery (SSRF) | 5.4 |

## OWASP Top 10 for LLM Applications (2025)
| # | Risk | Maps to 85-check |
|---|---|---|
| LLM01 | Prompt Injection | 8.2 |
| LLM02 | Sensitive Information Disclosure | 8.4, 1.1, 1.4 |
| LLM03 | Supply Chain Vulnerabilities | 9.1–9.4 |
| LLM04 | Data and Model Poisoning | 8.2, 8.5 |
| LLM05 | Improper Output Handling | 8.3 |
| LLM06 | Excessive Agency | 8.2 |
| LLM07 | System Prompt Leakage | 8.4 |
| LLM08 | Vector and Embedding Weaknesses | 8.5 |
| LLM09 | Misinformation | 8.3 |
| LLM10 | Unbounded Consumption | 8.1, 11.2 |

## How to use this file
- For each OWASP item, find its mapped 85-check area(s) and run those checks. Do not run OWASP items as a separate pass — they are the same checks, grouped by risk.
- If an LLM item has no equivalent in the app (e.g. no RAG, no tool use), mark it N/A with the evidence (searched code, no such feature).
- Sources: owasp.org/Top10/2025, genai.owasp.org/llm-top-10
