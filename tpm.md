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
| AMD fTPM | AGESA / PI firmware (platform-specific) | 🔴 Not Supported | Unknown | None | Firmware TPM 2.0 running on the AMD Secure Processor (ASP), delivered via OEM BIOS updates. No PQC support documented. See [AMD-SB-4011](https://www.amd.com/en/resources/product-security/bulletin/amd-sb-4011.html) for fTPM firmware versions per platform. |
| AWS NitroTPM | N/A (managed service) | 🔴 Not Supported | N/A (virtual) | None | Virtual TPM 2.0 provided by the AWS Nitro System for EC2 instances. No PQC support documented. [NitroTPM documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/nitrotpm.html). |
| COCONUT-SVSM vTPM | v2026.09-devel | 🔴 Not Supported | N/A (virtual) | None | Open-source vTPM running inside AMD SEV-SNP confidential VMs, built on the TCG reference implementation. No TPM 2.0 Library 1.85 PQC commands in the [command list](https://github.com/coconut-svsm/svsm/blob/v2026.09-devel/libtcgtpm/deps/TpmConfiguration/TpmConfiguration/TpmProfile_CommandList.h). |
| Google Cloud vTPM (Shielded VM) | N/A (managed service) | 🔴 Not Supported | N/A (virtual) | None | Per-VM virtual TPM for Shielded VMs and Confidential VMs. No PQC support documented. [Shielded VM documentation](https://docs.cloud.google.com/compute/shielded-vm/docs/shielded-vm). |
| Infineon OPTIGA TPM SLB 9665 | FW 5.80 (Library 1.16) | 🔴 Not Supported | PC Client (PTP 0.43) | None | Not recommended for new designs. Firmware updates signed with RSA-2048/SHA-256. No PQC support. Per [FIPS 140-2 Security Policy #2959](https://csrc.nist.gov/CSRC/media/projects/cryptographic-module-validation-program/documents/security-policies/140sp2959.pdf). |
| Infineon OPTIGA TPM SLB 9672/9673 | FW 15.xx | 🔴 Not Supported | PC Client (PTP 1.05) | None | PQC-protected firmware update mechanism using XMSS signatures. This protects the firmware update channel only. No PQC algorithm support for application cryptographic operations. [OPTIGA TPM SLB 9672 FW15 Datasheet](https://www.infineon.com/assets/row/public/documents/30/49/infineon-slb9672-tpm20-spi-fw15xx-ds-rev1-5-2024-11-13-datasheet-en.pdf). |
| Infineon OPTIGA TPM SLB/SLI/SLM 9670 (TPM 2.0) | FW 7.85 (SLB) / 13.11 (SLI, SLM) (Library 1.38) | 🔴 Not Supported | PC Client (PTP 1.03) | None | SLB 9670 is not recommended for new designs; SLI 9670 (automotive) and SLM 9670 (industrial) share the same 9670 family. Firmware updates verified with RSA-2048/SHA-256. No PQC support. Per FIPS 140-2 Security Policies [#3492 (SLB 9670)](https://csrc.nist.gov/CSRC/media/projects/cryptographic-module-validation-program/documents/security-policies/140sp3492.pdf) and [#3747 (SLI/SLM 9670)](https://csrc.nist.gov/CSRC/media/projects/cryptographic-module-validation-program/documents/security-policies/140sp3747.pdf). |
| Intel Platform Trust Technology (PTT) | CSME firmware (platform-specific) | 🔴 Not Supported | Unknown | None | Firmware TPM 2.0 running in the Intel CSME ([Core Ultra 200S datasheet](https://edc.intel.com/content/www/us/en/design/products/platforms/details/arrow-lake-s/core-ultra-200s-series-processors-datasheet-volume-1-of-2/intel-platform-trust-technology/)). CSME firmware signed with RSA (RSASSA-PSS RSA-3072 from CSME 15) per the [Intel CSME Security White Paper](https://web.archive.org/web/2023/https://www.intel.com/content/dam/www/public/us/en/security-advisory/documents/intel-csme-security-white-paper.pdf). No PQC support documented. |
| Microchip ATTPM20P | TCG FW rev116 | 🔴 Not Supported | PC Client (PTP 1.3) | None | No PQC support identified. |
| Microsoft Azure Confidential VM vTPM | N/A (managed service) | 🔴 Not Supported | N/A (virtual) | None | vTPM running inside the confidential VM's hardware-protected paravisor (AMD SEV-SNP / Intel TDX). No PQC support documented. [Azure confidential VM vTPM documentation](https://learn.microsoft.com/en-us/azure/confidential-computing/virtual-tpms-in-azure-confidential-vm). |
| Microsoft Azure vTPM (Trusted Launch) | N/A (managed service) | 🔴 Not Supported | N/A (virtual) | None | Virtual TPM 2.0 for Azure Trusted Launch VMs. No PQC support documented. [Trusted Launch documentation](https://learn.microsoft.com/en-us/azure/virtual-machines/trusted-launch). |
| Microsoft Hyper-V vTPM | Windows 10.0.19041 | 🔴 Not Supported | N/A (virtual) | None | Virtual TPM for Hyper-V Generation 2 VMs. No PQC algorithms listed. Per [FIPS 140-2 Security Policy #4537](https://csrc.nist.gov/CSRC/media/projects/cryptographic-module-validation-program/documents/security-policies/140sp4537.pdf). |
| Microsoft TPM 2.0 Reference Implementation (ms-tpm-20-ref) | v1.83r1 (Library 1.83) | 🔴 Not Supported | N/A (software) | None | TCG reference implementation used as the basis for many firmware TPMs. Latest release implements Library rev 1.83, which predates the PQC additions in 1.85. [Release v1.83r1](https://github.com/microsoft/ms-tpm-20-ref/releases/tag/v1.83r1). |
| Microsoft Pluton (as TPM) | Firmware via Windows Update | 🔴 Not Supported | Unknown | None | Integrated security processor that can serve as TPM 2.0. Beginning with 2026 silicon, Pluton no longer serves as the TPM on AMD and Qualcomm platforms. No PQC support documented. [Pluton as TPM](https://learn.microsoft.com/en-us/windows/security/hardware-security/pluton/pluton-as-tpm). |
| Nations Technologies Z32H330TC | FW 7.51 (Library 1.38) | 🔴 Not Supported | Unknown | None | Dual-mode TPM 2.0 / TCM 2.0. No PQC support identified. Per [NIST CAVP validated product #11204](https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/details?product=11204). |
| NSING NS350 | FW 30.30.9220.9488 (Library 1.59) | 🔴 Not Supported | Unknown | None | Dual-mode TPM 2.0 / TCM 2.0, Common Criteria EAL4+ (ANSSI-CC-2024/31). No PQC support identified. Per [NS350 Security Target](https://www.commoncriteriaportal.org/files/epfiles/ANSSI-cible-CC-2024_31en.pdf). |
| Nuvoton NPCT6xx (TPM 2.0) | FW 1.3.2.8 | 🔴 Not Supported | Unknown | None | Firmware updates verified with RSA-2048/SHA-256. No PQC support. Per [FIPS 140-2 Security Policy #2627](https://csrc.nist.gov/CSRC/media/projects/cryptographic-module-validation-program/documents/security-policies/140sp2627.pdf). |
| Nuvoton NPCT7xx | v1.16/1.38 | 🔴 Not Supported | PC Client (PTP 1.03) | None | No PQC support identified. |
| NVIDIA Jetson fTPM | Jetson Linux r38.4 | 🔴 Not Supported | N/A (firmware) | None | Firmware TPM running as an OP-TEE Trusted Application, built from the TCG reference implementation. No PQC support documented. [Jetson Firmware TPM documentation](https://docs.nvidia.com/jetson/archives/r38.4/DeveloperGuide/SD/Security/FirmwareTPM.html). |
| Qualcomm Snapdragon fTPM | Unknown | 🔴 Not Supported | Unknown | None | Firmware TPM 2.0 on 2026+ Snapdragon Windows platforms (replacing Pluton-as-TPM), per [Microsoft Pluton as TPM](https://learn.microsoft.com/en-us/windows/security/hardware-security/pluton/pluton-as-tpm). No Qualcomm technical documentation or PQC support found. |
| SEALSQ QVault TPM 183 | TPR1003B (Preliminary) | 🔴 Not Supported | PC Client (PTP 1.06) | None | ML-DSA used for firmware update signing only, not available for application TPM operations. Per [QVault TPM 183 Technical Datasheet](https://www.sealsq.com/hubfs/TPR1003B_10Aug26.pdf?hsLang=en). |
| SEALSQ QVault TPM 185 | TPR1026A (Preliminary) | 🟡 In Progress | PC Client (PTP 1.07) | ML-KEM/ML-DSA | ML-KEM and ML-DSA mandatory per [QVault TPM 185 Technical Datasheet](https://www.sealsq.com/hubfs/Data%20Sheets/QVaultTPM_185_Datasheet.pdf). FIPS 140-3 and TCG certification processes underway. Preliminary datasheet. |
| STMicroelectronics ST33GTPMA / ST33GTPMI | FW 3.512 (SPI) / 6.512 (I2C) (Library 1.38) | 🔴 Not Supported | PC Client (PTP 1.04) | None | Automotive (GTPMA) and industrial (GTPMI) variants. Firmware updates signed with RSASSA-PSS RSA-2048. No PQC support. Per [FIPS 140-2 Security Policy #4304](https://csrc.nist.gov/CSRC/media/projects/cryptographic-module-validation-program/documents/security-policies/140sp4304.pdf). |
| STMicroelectronics ST33KTPM2I | FW 10.512 (Library 1.59) | 🔴 Not Supported | PC Client (PTP 1.06) | None | Industrial variant. Firmware updates signed with ECDSA P-384 plus LMS (SP 800-208); this protects the firmware update channel only. No PQC algorithm support for application cryptographic operations. Per [FIPS 140-3 Security Policy #5103](https://csrc.nist.gov/CSRC/media/projects/cryptographic-module-validation-program/documents/security-policies/140sp5103.pdf). |
| STMicroelectronics ST33KTPM2X | v1.59 errata 1.5 | 🔴 Not Supported | PC Client (PTP 1.06) | None | Firmware update signed with LMS (SP800-208) per downloadable databrief but no PQC algorithm support for application cryptographic operations. |
| STMicroelectronics ST33TPHF20 | FW 4A.40 (Library 1.38) | 🔴 Not Supported | PC Client (PTP 1.03) | None | Firmware updates verified with RSASSA-PSS RSA-2048. No PQC support. Per [FIPS 140-2 Security Policy #3682](https://csrc.nist.gov/CSRC/media/projects/cryptographic-module-validation-program/documents/security-policies/140sp3682.pdf). |
| STMicroelectronics ST33TPHF2E (TPM 2.0 mode) | FW 49.14 (SPI) / 49.15 (I2C) | 🔴 Not Supported | PC Client (PTP 0.43) | None | Dual-mode TPM 1.2 / 2.0. No PQC support. Per [FIPS 140-2 Security Policy #3681](https://csrc.nist.gov/CSRC/media/projects/cryptographic-module-validation-program/documents/security-policies/140sp3681.pdf). |
| STMicroelectronics ST33TPHF2X | FW 1.769 (Library 1.59) | 🔴 Not Supported | PC Client (PTP 1.04) | None | Firmware updates signed with RSASSA-PSS RSA-2048. No PQC support. Per [FIPS 140-2 Security Policy #4304](https://csrc.nist.gov/CSRC/media/projects/cryptographic-module-validation-program/documents/security-policies/140sp4304.pdf). |
| STMicroelectronics STSAFE-V100-TPM (ST33KTPM2A) | FW 10.512 (Library 1.59) | 🔴 Not Supported | PC Client (PTP 1.06) | None | Automotive variant, referred to as ST33KTPM2A in certification documents. Firmware updates signed with ECDSA P-384 plus LMS (SP 800-208); this protects the firmware update channel only. No PQC algorithm support for application cryptographic operations. Per [FIPS 140-3 Security Policy #5103](https://csrc.nist.gov/CSRC/media/projects/cryptographic-module-validation-program/documents/security-policies/140sp5103.pdf). |
| swtpm / libtpms | libtpms v0.10.2 (Library 1.83) | 🔴 Not Supported | N/A (software) | None | Software TPM emulator used as the vTPM backend for QEMU/libvirt. No 1.85 PQC commands in the [libtpms command list](https://github.com/stefanberger/libtpms/blob/v0.10.2/src/tpm2/TpmProfile_CommandList.h). [libtpms v0.10.2](https://github.com/stefanberger/libtpms/releases/tag/v0.10.2). |
| VMware vSphere vTPM | vSphere 9.0 | 🔴 Not Supported | N/A (virtual) | None | Per-VM virtual TPM 2.0 implemented by ESXi. No PQC support documented. [vSphere vTPM documentation](https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/9-0/vsphere-security/securing-virtual-machines-with-virtual-trusted-platform-module/vtpm-overview.html). |
| wolfSSL wolfTPM fwTPM | v4.1.0+ | 🟢 Ready | N/A (software) | ML-KEM-512/768/1024, ML-DSA-44/65/87 | Firmware/software TPM added in v4.0.0. TPM 2.0 Library 1.85 PQC commands (Encapsulate, Decapsulate, SignDigest, VerifyDigestSignature, Sign/Verify sequences) added in v4.1.0 per [ChangeLog](https://github.com/wolfSSL/wolfTPM/blob/v4.1.0/ChangeLog.md) and [fwTPM command table](https://github.com/wolfSSL/wolfTPM/blob/v4.1.0/src/fwtpm/fwtpm_command.c). Not FIPS 140-3 validated. |

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
