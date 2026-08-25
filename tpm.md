# PQC Readiness Tracker: Trusted Platform Modules (TPMs)

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

**_Seed data for working out formatting and collected details. This is not complete or fully vetted._**

## TPM Status Registry

| TPM Model | Version | Status | TCG Profile | Supported PQC Algorithms | Notes / Trackers |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [Example TPM] | 1.0 | 🔴 Not Supported | N/A | None | Link to issue/PR |
| Infineon OPTIGA TPM SLB 9672/9673 | FW 15.xx | 🔴 Not Supported | PC Client (PTP 1.05) | None | PQC-protected firmware update mechanism using XMSS signatures. This protects the firmware update channel only. No PQC algorithm support for application cryptographic operations. [OPTIGA TPM SLB 9672 FW15 Datasheet](https://www.infineon.com/assets/row/public/documents/30/49/infineon-slb9672-tpm20-spi-fw15xx-ds-rev1-5-2024-11-13-datasheet-en.pdf). |
| Microchip ATTPM20P | TCG FW rev116 | 🔴 Not Supported | PC Client (PTP 1.3) | None | No PQC support identified. |
| Nuvoton NPCT7xx | v1.16/1.38 | 🔴 Not Supported | PC Client (PTP 1.03) | None | No PQC support identified. |
| SEALSQ QVault TPM 183 | TPR1003B (Preliminary) | 🔴 Not Supported | PC Client (PTP 1.06) | None | ML-DSA used for firmware update signing only, not available for application TPM operations. Per [QVault TPM 183 Technical Datasheet](https://www.sealsq.com/hubfs/TPR1003B_10Aug26.pdf?hsLang=en). |
| SEALSQ QVault TPM 185 | TPR1026A (Preliminary) | 🟢 Ready | PC Client (PTP 1.07) | ML-KEM/ML-DSA | ML-KEM and ML-DSA mandatory per [QVault TPM 185 Technical Datasheet](https://www.sealsq.com/hubfs/Data%20Sheets/QVaultTPM_185_Datasheet.pdf). FIPS 140-3 and TCG certification processes underway. Preliminary datasheet. |
| STMicroelectronics ST33KTPM2X | v1.59 errata 1.5 | 🔴 Not Supported | PC Client (PTP 1.06) | None | Firmware update signed with LMS (SP800-208) per downloadable databrief but no PQC algorithm support for application cryptographic operations. |

Status: 🟢 Ready / 🟡 In Progress / 🔴 Not Supported


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
* Focus on TPM 2.0 implementations. TPM 1.2 has no path to PQC support.