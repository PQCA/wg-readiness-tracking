# Network Equipment Readiness

This is a first pass that was AI generated (via a combination of Gemini and Claude) and then adjusted lightly. It has not been human vetted in a meaningful way yet.

Should we shift to device class first (Firewall, Router, Switch, VPN...). Nest device types within vendors. 

## Arista Networks

| Equipment Family | OS / Version | Secure Boot & Image Integrity | Management Plane (SSH/TLS) | Data Plane (IPsec/MACsec) | Notes / Citations |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **All EOS Platforms** | EOS 4.36.1F+ | 🟣 **Unknown** | 🟢 **Ready:** ML-KEM & X25519MLKEM768 SSL Profiles | 🟡 **Partial:** AES-256 MACsec | EOS Control Plane Security allows configuring pure (MLKEM768) and hybrid (SecP256r1MLKEM768) PQC KEMs for switch management. [EOS 4.36.1F Manual, July 2026] |
| **7800R3 Series** | EOS | 🟣 **Unknown** | 🟣 **Unknown** | 🟡 **Partial:** 100G/400G Line-rate MACsec | Relying on classical AES-256-GCM. Hardware acceleration present but IPsec/MACsec key exchange remains classical unless managed via QKD/external key servers. [Arista 7800R3 Datasheet] |

## Check Point

| Equipment Family | OS / Version | Secure Boot & Image Integrity | Management Plane (SSH/TLS) | Data Plane (IPsec/MACsec) | Notes / Citations |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Quantum Security Gateways** | R82 | 🟡 **Roadmap:** SIC Crypto-agility built-in | 🟣 **Unknown** | **Ready (Hybrid):** QSKE (RFC 9370/9242) ML-KEM | R82 delivers Quantum-Safe Key Exchange (QSKE) for Site-to-Site VPNs. [Check Point R82 Release Notes, Nov 2024/2025] |
| **Quantum Gateways (SSL)** | R82.10 (EA) | **N/A** | 🟢 **Ready:** X25519MLKEM768 Inspection | **N/A** | Allows passing transparently or inspecting PQC TLS. If unsupported, drops connection. [Check Point Blog, Sept 2025] |

## Cisco Systems

*Note: Cisco's "Full Stack PQC" architecture aligns with the IOS XE 26 and IOS XR 26 release branches.*

| Equipment Family | OS / Version | Secure Boot & Image Integrity | Management Plane (SSH/TLS) | Data Plane (IPsec/MACsec) | Notes / Citations |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Catalyst 9350 / 9610 Switches** | IOS XE 26.x | 🟡 **Roadmap:** ML-DSA & LMS signing (H2 2026) | 🟡 **Roadmap:** ML-KEM integration | 🟡 **Roadmap:** MACsec AES-256 (H1 2026), IPsec IKEv2 ML-KEM (H2 2026) | Hardware root of trust relies on Trust Anchor module (TAm). [Cisco Live 2026] |
| **8000 Series Secure Routers** | IOS XR 26.1.1+ | 🟣 **Unknown** | 🟣 **Unknown** | 🟢 **Ready (Hybrid):** IKEv2 ML-KEM-768 support. | Interoperability validated with Cloudflare IPsec tunnels. [Cloudflare Docs, April 2026] |
| **Legacy Catalyst / ISR** | IOS XE 17.x | 🔴 **Not Supported** | 🔴 **Not Supported** | 🟡 **Partial:** RFC 8784 (PPK) support | PPK allows classical IPsec to mix in out-of-band quantum-safe secrets. |
| Catalyst 9500 Series Switches | IOS-XE 26.1.1+ | ? | 🟡 In Progress | ML-KEM, LMS, ML-DSA-87 | Supports PQC MACsec and secure boot verification. |
| Catalyst 9600 Series Switches | IOS-XE 26.1.1+ | ? | 🟡 In Progress | ML-KEM, LMS, ML-DSA-87 | PQC MACsec support for Layer 2 LAN edge protection. |
| Catalyst 9400 Series Switches | IOS-XE 26.1.1+ | ? | 🟡 In Progress | ML-KEM, LMS, ML-DSA-87 | Hardware-rooted chain of trust via Trust Anchor module (TAm). |
| Catalyst 9300 Series Switches | IOS-XE 26.1.1+ | ? | 🟡 In Progress | ML-KEM, LMS, ML-DSA-87 | Implements quantum-resistant signature algorithms. |
| Catalyst 9200 Series Switches | IOS-XE | ? | 🔴 Not Supported | N/A | Roadmap evaluation pending for lower-end access models. |
| 8100 Series Secure Router | IOS-XR / 26.1.1+ | ? | 🟢 Ready | ML-KEM, Hash-Based Sigs (HBS) | Provides quantum-safe secure boot (HBS precursor to LMS). |
| 8200 Series Secure Router | IOS-XR / 26.1.1+ | ? | 🟢 Ready | ML-KEM, ML-DSA-87, LMS | IKEv2/IPsec VPN key exchange using ML-KEM (FIPS 203). |
| 8800 Series Secure Router | IOS-XR / 26.1.1+ | ? | 🟢 Ready | ML-KEM, ML-DSA-87, LMS | Silicon One powered. Full-stack PQC architecture. |
| Secure Firewall 4215 | FTD / FXOS | ? | 🟢 Ready | Hash-Based Sigs (HBS) | Secure boot verified via quantum-resistant algorithms. |
| Secure Firewall 7100 Series | FTD / FXOS | ? | 🟡 In Progress | Hybrid PQC | Integration for PQC VPN and telemetry in progress. |
| Secure Firewall 3100 Series | FTD / FXOS | ? | 🟡 In Progress | Hybrid PQC | Next-gen cryptographic transition planned. |

## F5 Networks

| Equipment Family | OS / Version | Secure Boot & Image Integrity | Management Plane (SSH/TLS) | Data Plane (IPsec/MACsec) | Notes / Citations |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **BIG-IP System** | TMOS v17.5.1+ / v21.1 | 🟣 **Unknown** | 🟢 **Ready:** X25519MLKEM768 | 🟢 **Ready:** L7 Proxy / SSL Offload | Requires explicit TLS 1.3 configuration. Deprecated draft Kyber for NIST ML-KEM. Often deployed in front of object storage (NetApp) to stop harvesting. [F5 KB K000149577 / K000161408] |
| **NGINX Plus** | R33+ | 🟣 **Unknown** | 🟢 **Ready:** ML-KEM768 (OQS) | 🟢 **Ready:** L7 Proxy | Requires manual enablement in the configuration. [F5 Labs PQC Web Report] |

## Fortinet

| Equipment Family | OS / Version | Secure Boot & Image Integrity | Management Plane (SSH/TLS) | Data Plane (IPsec/MACsec) | Notes / Citations |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **FortiGate NGFW** | FortiOS 8.0.0 / 7.6.6 | 🟣 **Unknown** | 🟢 **Ready:** HTTPS/SSH PQC algorithms | 🟢 **Ready (Hybrid):** ML-KEM-512/768/1024 for IPsec | Implements RFC 9370/9242 (ADDKE). Interoperable with Cloudflare IPsec. [FortiOS 8.0 Release Notes; Cloudflare April 2026] |
| **FortiGate (SSL Inspection)** | FortiOS 7.6.5+ | **N/A** | 🟢 **Ready:** X25519MLKEM768 Deep Inspection | **N/A** | Supports hybrid PQC key exchanges in SSL deep inspection (flow mode) for Chrome 138+ compatibility. [FortiOS 7.6.5 Release Notes] |

## HPE Aruba & Extreme Networks

| Equipment Family | OS / Version | Secure Boot & Image Integrity | Management Plane (SSH/TLS) | Data Plane (IPsec/MACsec) | Notes / Citations |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **HPE Aruba CX Switches** | AOS-CX | 🟣 **Unknown** | 🟣 **Unknown** | 🟡 **Partial:** AES-256 MACsec | No public roadmap data for native ML-KEM/ML-DSA integration in AOS-CX as of mid-2026. |
| **Extreme Networks 5420/5720** | EXOS / VOSS | 🟣 **Unknown** | 🟣 **Unknown** | 🟡 **Partial:** AES-256 MACsec | No public roadmap data for native ML-KEM/ML-DSA integration. |


## Juniper Networks (HPE)

| Equipment Family | OS / Version | Secure Boot & Image Integrity | Management Plane (SSH/TLS) | Data Plane (IPsec/MACsec) | Notes / Citations |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **ACX, PTX, & QFX Series** | Junos OS Evolved 25.4+ | 🟢 **Ready:** ML-DSA-87 (Off-box verification) | 🟢 **Ready (Mitigation):** "Quantum Buffer" for SSH | **Partial:** Out-of-band QKD API | CNSA 2.0 compliant image signatures. SSH uses a finite-field buffer rather than pure ML-KEM. [Junos EVO 25.4 Release Notes] |
| **SRX Series Firewalls** | Junos OS 22.4R1+ | 🟡 **Roadmap:** FIPS 204 signing (2026) | 🟡 **Roadmap** | 🟢 **Ready (Hybrid):** QKD Integration & PPK (RFC 8784) | Supports dynamic fetching of quantum keys from QKD devices for MACsec/IPsec. [Juniper SRX Docs] |
| PTX10000 Series Routers | Junos OS EVO 25.4+ | | 🟢 Ready | sntrup761, X25519, ML-DSA-87 | Shor-resistant SSH key exchange; off-box PQC image verification. |
| PTX10008 Router | Junos OS EVO 25.4+ | | 🟢 Ready | sntrup761, ML-DSA-87 | CNSA 2.0 compliant digital signatures for OS integrity. |
| ACX7000 Series Routers | Junos OS EVO 25.4+ | | 🟢 Ready | sntrup761, X25519, ML-DSA-87 | Quantum Buffer in SSH limits FFC vulnerability. |
| ACX5000 Series Routers | Junos OS EVO 25.4+ | | 🟢 Ready | sntrup761, X25519 | Hybrid classical/post-quantum SSH support. |
| QFX10000 Series Switches | Junos OS / EVO | | 🟢 Ready | sntrup761, ML-DSA-87 | MACsec and SSH PQC implementations enabled. |
| QFX5200 Series Switches | Junos OS / EVO | | 🟢 Ready | sntrup761, ML-DSA-87 | PQC-signed Junos OS Evolved software images. |
| QFX5100 Series Switches | Junos OS / EVO | | 🟡 In Progress | sntrup761 | Partial rollout depending on specific image capabilities. |
| MX960 Universal Router | Junos OS | | | 🟡 In Progress | QKD API, Hybrid PQC | Integrates with Quantum Key Distribution (QKD) via ETSI GS QKD 014. |
| MX10003 Universal Router | Junos OS | | 🟡 In Progress | QKD API, Hybrid PQC | IPsec VPN/MACsec integration with QKD and EvolutionQ. |
| SRX5000 Series Firewalls | Junos OS | | 🟡 In Progress | Post-Quantum PPK | IKEv2 RFC 8784 post-quantum preshared keys (PPKs) support. |
| SRX4000 Series Firewalls | Junos OS | | 🟡 In Progress | Post-Quantum PPK | Post-quantum VPN security scaling. |
| SRX1500 Firewall | Junos OS | | 🟡 In Progress | Post-Quantum PPK | Out-of-band key mechanisms and PPK mixing. |

## Nokia & Ciena (Service Provider / Optical Edge)

| Equipment Family | OS / Version | Secure Boot & Image Integrity | Management Plane (SSH/TLS) | Data Plane (IPsec/MACsec) | Notes / Citations |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Nokia 7750 SR / SR OS** | SR OS / SR Linux | 🟣 **Unknown** | 🟣 **Unknown** | 🟢 **Ready (Hybrid):** IPsec RFC 9370 & ANYsec | Tightly integrates with NetGuard Certificate Manager and supports external QKD via ETSI APIs. [Nokia PQC Application Notes, Jan 2026] |
| **Ciena Waveserver 5** | WaveLogic 6 | 🟣 **Unknown** | 🟣 **Unknown** |  🟢 **Ready:** L1 Optical PQC & QKD | Wire-speed Layer 1 optical encryption scaling up to 1.6Tbps supporting NIST-certified PQC algorithms and QKD system interworking. [Ciena WaveLogic 6 Specs] |

## Palo Alto Networks

| Equipment Family | OS / Version | Secure Boot & Image Integrity | Management Plane (SSH/TLS) | Data Plane (IPsec/MACsec) | Notes / Citations |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **PA-Series NGFW** | PAN-OS 12.1 / 11.2 | 🟣 **Unknown** | 🟢 **Ready:** Quantum Readiness Telemetry | **Ready (Hybrid):** Multi-KEM IKEv2 | Uses RFC 9242/9370 to negotiate multiple successive key exchanges, mixing ECDH with PQC KEMs. [PAN-OS TechDocs] |
| **Prisma SASE / Edge** | PAN-OS 12.1 | 🟣 **Unknown** | 🟣 **Unknown** | **Ready:** Quantum-Safe Cipher Translation | Proxies legacy classical apps over quantum-safe tunnels. |
| PA-5500 Series NGFW | PAN-OS 12.1 Orion | ? | 🟢 Ready | ML-KEM, PQC KEMs | Built to decrypt and inspect PQC-encrypted TLS traffic. |
| PA-5400 Series NGFW | PAN-OS 12.1 Orion | ? | 🟢 Ready | ML-KEM, PQC KEMs | Cipher translation feature upgrades legacy app sessions. |
| PA-3400 Series NGFW | PAN-OS 12.1 Orion | ? | 🟢 Ready | ML-KEM, PQC KEMs | Quantum Readine


## Ubiquiti

| Equipment Family | OS / Version | Secure Boot & Image Integrity | Management Plane (SSH/TLS) | Data Plane (IPsec/MACsec) | Notes / Citations |
| :--- | :--- | :--- | :--- | :--- | :--- |

---

## Guidance
* **Hybrid Mode Requirement:** Currently, pure PQC deployments are not as far along in standards bodies. All "Ready" statuses for IPsec/TLS refer to the implementation of **hybrid key exchanges** (e.g., X25519 + ML-KEM-768) via RFCs 9370, 9242, and 8784.
* **Algorithm Specificity:** Where possible, list the exact parameter set (e.g., ML-KEM-768 vs KyberDraft) as support is rapidly shifting.


1. Cisco Live 2026: BRKENS-1855 "Enabling PQC on C9000 Smart Switches"

2. Cloudflare: Cisco IOS XE - Cloudflare WAN IPsec Integration (Tested May 2026) - https://developers.cloudflare.com/cloudflare-wan/configuration/third-party/cisco-ios-xe/

3. Juniper Networks: Junos OS Evolved 25.4 Release Notes (Dec 2025) - https://www.juniper.net/documentation/us/en/software/junos/release-notes/25.4/junos-evo-release-notes-25.4r1/topics/new-features/feature-descriptions/Post-Quantum-Cryptography.html

4. HPE/Juniper: HPE RSA Conference Announcements (March 2026) - https://www.hpe.com/us/en/newsroom/press-release/2026/03/hpe-introduces-sweeping-security-advancements-to-secure-ai-adoption-and-strengthen-enterprise-resiliency.html

5. Palo Alto Networks: PAN-OS 12.1 Orion PQC Features (Aug 2025) - https://quantumcomputingreport.com/palo-alto-networks-introduces-pan-os-12-1-orion-with-post-quantum-cryptography-features/

6. Palo Alto TechDocs: Support for Post-Quantum Features - https://docs.paloaltonetworks.com/network-security/quantum-security/administration/quantum-security-concepts/support-for-quantum-features
