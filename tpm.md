# PQC Readiness Tracker: Trusted Platform Modules (TPMs)

**The Working Group has not settled on the final format, this version 
is an early draft intended to solicit input.**

These pages track the state of Post-Quantum Cryptography (PQC) readiness 
for Trusted Platform Modules (TPMs). This is a crowdsourced effort; please 
contribute by adding details about items you maintain or have reliable 
knowledge of.

## Background

The [TCG PC Client Platform TPM Profile (PTP) 1.07](https://trustedcomputinggroup.org/wp-content/uploads/PC-Client-Specific-Platform-TPM-Profile-for-TPM-2p0-v1p07_Pub.pdf) 
defines the baseline for PQC-ready TPMs. ML-KEM and ML-DSA are mandatory 
as of PTP 1.07. TCG has defined two transition designations:

- **TCG PQC-ready TPM** — implements PTP 1.07
- **TCG PQC-upgradable TPM** — does not currently support PTP 1.07 but 
  can be upgraded via firmware

## TPM Status Registry

| TPM Model | Version | Status | TCG Designation | Supported PQC Algorithms | Notes / Trackers |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [Example TPM] | 1.0 | 🔴 Not Supported | N/A | None | Link to issue/PR |

Status: 🟢 Ready / 🟡 In Progress / 🔴 Not Supported

## Readiness Criteria

- **Inventory**: Does the TPM identify all non-PQC cryptographic dependencies?
- **Algorithm Support**: Does it support NIST-standardized PQC algorithms?
- **Agility**: Can the TPM switch between classical, hybrid, and PQC-only modes?

### Status Definitions

- 🟢 **Ready**: at least 1 NIST-standardized key exchange algorithm (e.g. ML-KEM) AND at least 1 NIST-standardized signature algorithm (e.g. ML-DSA) are supported.
- 🟡 **In Progress**: only one of the two (key exchange OR signature) is supported, or support is in development/unreleased.
- 🔴 **Not Supported**: neither is supported.

## How to Contribute

1. Fork this repo.
2. Update the table above with new information or edits.
3. Submit a Pull Request with the tag `[PQC-Readiness]`.

## Guidance

* All linked information should point to an official repository or technical documentation. If you provide a link to a press release or product page, you will be asked to provide a different link.
* Include firmware version numbers where PQC support was introduced.
* Distinguish between PQC support for application cryptographic operations and PQC-protected firmware update mechanisms — these are not the same thing.
* Note the TCG designation (PQC-ready or PQC-upgradable) where known, per [TCG guidance](https://trustedcomputinggroup.org/wp-content/uploads/PC-Client-Specific-Platform-TPM-Profile-for-TPM-2p0-v1p07_Pub.pdf).
* Focus on TPM 2.0 implementations. TPM 1.2 is end of life and should be noted as Not Supported without further detail.