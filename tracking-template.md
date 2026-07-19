# PQC Readiness Tracking Template

**The Working Group has not settled on the final format, this version is an early draft intended to solicit input.**

These pages track the state of Post-Quantum Cryptography (PQC) readiness for common libraries, software and hardware. This is a crowdsourced effort; please contribute by adding details about items you maintain or have reliable knowledge of.

## Library Status Registry

| Library Name | Version | Status | Supported Algorithms | Notes / Trackers |
| :--- | :--- | :--- | :--- | :--- |
| [Example Library] | 1.0 | 🔴 Not Supported | ML-KEM, ML-DSA, ... | Link to issue/PR |
| | | | | |

Status:  🟢 Ready / 🟡 In Progress / 🔴 Not Supported

* N.B. if you are forking this page for a new use case, update the heading before the table and first column name in the table to reflect the use case.

## Readiness Criteria
- **Inventory**: Does the package identify all non-PQC cryptographic dependencies?
- **Algorithm Support**: Does it support NIST-standardized PQC algorithms?
- **Agility**: Can the package switch between classical, hybrid, and PQC-only modes?

## How to Contribute
1. Fork this repo.
2. Update the table above with new information or edits.
3. Submit a Pull Request with the tag `[PQC-Readiness]`.

## Guidance
* All linked information should point to an official repository or technical documentation. If you provide a link to a press releases or product page, you will be asked to provide a different link.
