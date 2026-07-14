# PQC Readiness Tracking - HSMs

## Test Page, data has not been fully vetted

These pages track the state of Post-Quantum Cryptography (PQC) readiness for common libraries, software and hardware. This is a crowdsourced effort; please contribute by adding details about items you maintain or have reliable knowledge of.

## Hardware Security Modules

| HSM Model | Version | PQC Status | FIPS 140-3 L3 Status | Supported PQC Algorithms | Notes / Trackers |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [Example HSM] | 1.0 | 🔴 Not Started | 🟡 In Progress | ML-KEM, ML-DSA, ... | Summary or link to issue/PR |
| Crypto4A QxHSM™ (Blade Modules / Chassis) | Quantum-Safe FW Architecture | 🟢 Ready | 🟡 [In Progress](https://csrc.nist.gov/Projects/cryptographic-module-validation-program/modules-in-process/modules-in-process-list) |  Classic McEliece, HSS (max 8 subtrees), LMS, ML-DSA, ML-KEM, SHA2/SHAKE, SLH-DSA, XMSS | Modular 5th-generation HSM. Crypto agility for algorithm variations; FIPS 140-3 Level 3 evaluation in CMVP comment resolution. |
| Entrust nShield 5 / nShield Connect / nShield Solo | Firmware v13+ | 🟢 Ready | 🟡 In Progress | LMS, ML-DSA, ML-KEM, SLH-DSA, XMSS | FPGA acceleration for  classical, hybrid, and PQC. |
| nShield XC (XC Connect and XC Solo) | Firmware v13+ | 🟢 Ready | 🟣 Will not support | LMS, ML-DSA, ML-KEM, SLH-DSA | No PQC acceleration. |
| Entrust nShield Connect+ / Solo+ (Legacy Non-XC M-Series) | All v11 / v12 firmware | 🟣 Will not support | 🟣 Will not support | None | Legacy hardware builds lack the memory and processing capacity required to host the v13+ Security World architecture. No firmware upgrade path to PQC available. |
| Eviden (Atos) | Trustway Proteccio | 🟢 Ready | EAL4+ | ML-DSA, ML-KEM, SLH-DSA | EU focused |
| Fortanix FX2200 | ? | Unknown | 🟢 Ready | Unknown | Unknown |
| Futurex Excrypt Plus | 7.8+ | 🟢 Ready | FIPS 140-2 Level 3 and PCI HSM v3 |	ML-DSA, ML-KEM |Legacy Payment HSM platform with PCI-HSM validated PQC firmware for ML-DSA and ML-KEM. Supports staged migration using hybrid classical/PQC designs, HSM-backed key generation and signing operations. |
| Futurex Excrypt HSM | 8.0+ | 🟢 Ready | FIPS 140-3 Level 3 and PCI HSM v4 | ML-DSA, ML-KEM, SLH-DSA, LMS, HSS, XMSS |	Next-generation General Purpose and Payments HSM platform for enterprise cryptography, PKI, CA, code signing, and key management use cases. Supports HSM-backed PQC and hybrid certificate authority workflows, hybrid classical/PQC migration modes, PKCS#11 v3.2 PQC mechanisms, Microsoft CNG/KSP integration for Windows Server 2025, and tested interoperability with common PQC libraries. |
| Futurex Excrypt SSP Enterprise v.2 | 7.8+ | 🟢 Ready | FIPS 140-2 Level 3 and PCI HSM v3	| ML-DSA, ML-KEM | Legacy Enterprise payment HSM platform with PCI-HSM validated PQC firmware for ML-DSA and ML-KEM. Utilized by organizations that deploy larger payment cryptography environments.  Supports staged migration using hybrid classical/PQC designs, HSM-backed key generation and signing operations. |
| Futurex Vectera Plus | 7.8+ / 8.0+ | 🟢 Ready | FIPS 140-2 Level 3 and PCI HSM v3 / FIPS 140-3 Level 3 and PCI HSM v4 | ML-DSA, ML-KEM, SLH-DSA, LMS, HSS, XMSS | General purpose HSM platform for enterprise cryptography, PKI, CA, code signing, and key management use cases. Supports HSM-backed PQC and hybrid certificate authority workflows, hybrid classical/PQC migration modes, PKCS#11 v3.2 PQC mechanisms, Microsoft CNG/KSP integration for Windows Server 2025, and tested interoperability with common PQC libraries. |
| i4p Trident HSM | Quantum-Safe Package | 🟢 Ready | 🟡 In Progress | SLH-DSA | Common Criteria EAL4+ / eIDAS-listed network appliance. |
| IBM | Crypto Express (CEX8S) / IBM 4769 | ? | 🟢 Ready | ML-DSA & LMS/XMSS | Mainframe Transaction Signing |
| Marvell LiquidSecurity 2 (LS2) | Firmware v10.0+ | 🟡 In Progress | 🟢 Ready | ML-DSA, ML-KEM | PQC algorithms are currently supported in non-FIPS mode via the LS-SW-PQC software pack. |
Marvell LiquidSecurity 1 (LS1) / Cavium NITROX | N/A | 🔴 Not Started	| 🟢 Ready | None | Legacy models (certified to FIPS 140-2 and 140-3 Level 3); no PQC support has been announced |
| Thales Luna Network HSM 7 / PCIe HSM 7 | Firmware 7.7.0+ (Luna Client 10.7.1+) | 🟢 Ready | 🟢 Ready | LMS, ML-DSA, ML-KEM, SLH-DSA, XMSS | Accessible natively via core firmware updates or via the Luna PQC Functionality Module (FM) Toolkit 3.1. |
| Thales payShield 10K | Firmware 2.0a+ | 🟣 Will not support  | 🟣 Will not support | Tracking PCI HSM v4/v5 specifications | Payment ecosystem HSM actively tracking transition timelines and hybrid signature evaluation for financial transaction processing. |
| Thales SafeNet Luna Network HSM 5 / 6 (Luna SA 5 / 6) | All Versions / EOL | 🟣 Will not support | 🟣 Will not support | None | Legacy hardware architectural limits (CPU and cryptographic chipsets) prevent the execution of large-key PQC algorithms. Officially EOL. |
| Utimaco / Atalla AT1000 | Firmware 8.xx+ / 8.60+ | 🟣 Will not support  | 🟢 Ready | None | High-performance payment processing and cardholder authentication HSM. |
| Utimaco / Atalla A8000 / A9000 (Ax100 Series) | All Versions / EOL | 🟣 Will not support | 🟣 Will not support | None | Legacy transaction processing modules. These fixed-function cryptographic appliances cannot be modified or patched to compute post-quantum math. Hardware replacement required. |
| Utimaco CryptoServer Se-Series Gen1 / CryptoServer LAN | Firmware v4.x and below | 🟣 Will not support | 🟣 Will not support | None | Early generation general-purpose units. Limited internal flash memory capacity and lack of modern crypto-agility frameworks prevent the ingestion of PQC algorithms. |
| Utimaco u.trust General Purpose HSM (Se-Series & CSe-Series)| Quantum Protect Package | 🟢 Ready | 🟢 Ready | HSS, LMS, ML-DSA, ML-KEM, XMSS | offers a free  export-compliant Quantum Protect Simulator. |
| Yubico YubiHSM 2 | v2.4+ | 🟡 In Progress | 🟣 Will not support | PQC in pilot testing | Designed for low-volume root protection. |


Status:  🟢 Ready / 🟡 In Progress / 🔴 Not Started / 🟣 Will not support
