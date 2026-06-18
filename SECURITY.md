# Security Policy
As CARBON, we take security seriously. This page explains **how to report vulnerabilities privately**, what’s **in scope** for the open-source code we publish on GitHub, and **what you can expect from us**.

---
## Scope
This policy applies to **all public repositories under the `carbonengine` GitHub organization** and any packages/images we publish from those repos.
It does **not** cover FC’s production game services or player accounts (EVE Online, Vanguard, etc.). If your finding relates to FC games or live services, please follow the company’s Vulnerability Disclosure Program and contact **security@fenris.com**.

---
## How to Report
- **Please DO NOT open a public issue for security problems.**  
  Email **security@fenris.com** with the subject line:  
  `Vulnerability Report: <brief description>`
Include as much detail as you can:
- Commit hash or release tag
- Steps to reproduce (from a clean clone)
- Technical details (logs, requests/responses, payloads)
- Impact (what an attacker could achieve)
- Environment (OS, compiler/interpreter, build system)
- Your contact info and whether you prefer to remain anonymous
If you’re unsure whether something qualifies as a security issue, **send it anyway** and we’ll help triage.

### AI-generated reports. 
We **do not** accept vulnerability reports that appear to be unverified AI output, generic "potential" issues without a working reproduction. AI tools are fine for analysis however, the report itself must come from a human who has verified the issue, can reproduce it from a clean clone, and can discuss it. Reports that fail this bar will be closed without detailed triage.

---
## Our Process & Timelines
- **Acknowledgement:** We aim to respond within **3 business days**.
- **Triage:** Initial validity/severity review within **7 business days**.
- **Fix:** We prioritise based on impact and complexity. For critical issues, we work to validate within 14 days and target a fix as quickly as feasible.
- **Coordinated disclosure:** By default, we ask for **up to 90 days** from validation to publish details, but we’ll coordinate with you on timing.
- **Credit:** With your permission, we may acknowledge you in release notes or a SECURITY.md “Thanks” section.
For sensitive reports, we may use GitHub **Security Advisories** to collaborate privately until a fix is released.
---
## Supported Versions
We provide security fixes for:
- The `main` branch
- The most recent tagged release per repository
Older releases, archived modules, or forks are **not** supported for security patches.
---
## Out of Scope (Carbon OSS)
The following are **not** considered security issues for this policy:
- Bugs/crashes with **no security impact**
- **DoS** via oversized inputs, fuzzing, or load tests
- Findings that require access only to **your own** account/data
- **Third-party dependency** vulnerabilities (please report upstream); if they impact Carbon, include the specific exploit path
- **Social engineering** or phishing
- Issues in **FC's production services** (report to **security@fenris.com** under the main VDP instead)
If in doubt, ask us first at **security@fenris.com**.
---
## After a Fix
When a fix is ready, we will:
- Patch and publish a **tagged release** if applicable
- Note the issue in **CHANGELOG**/**release notes**, where appropriate, open a **GitHub Security Advisory**
- Coordinate public disclosure timing with the reporter
---
## Contact
- **Primary:** security@fenris.com  
- **Back-up (non-sensitive questions):** open an Issue in the relevant repo
Thank you for helping keep Carbon (and the developers who depend on it) safe.
