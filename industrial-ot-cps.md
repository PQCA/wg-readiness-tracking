# PQC Readiness Tracker: Industrial Operational Technology (OT) and Cyber-Physical Systems (CPS)

This page tracks the state of Post-Quantum Cryptography (PQC) readiness for industrial Operational Technology (OT) and Cyber-Physical Systems (CPS).

This includes industrial controllers and field-connected systems such as PLCs, RTUs, DCS and safety controllers, industrial gateways, and associated management platforms. These systems often have long service lives, constrained compute resources, vendor-dependent update paths, and strict availability and safety requirements.

This is a crowdsourced effort; please contribute information about products you maintain or for which you have reliable, public technical evidence.

## OT/CPS Status Registry

| Device / Product Family | Manufacturer | Firmware / Version | Status | Deployment Role | Supported PQC Algorithms | Notes / Trackers |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Example industrial controller | Example vendor | 1.0 | 🔴 Not Supported | PLC / RTU / gateway | None | Link to official technical documentation, issue, or PR |

Status: 🟢 Ready / 🟡 In Progress / 🔴 Not Supported

### Status Definitions

- 🟢 **Ready**: supports at least one NIST-standardized PQC key-establishment algorithm and one NIST-standardized PQC signature algorithm for relevant product cryptographic operations.
- 🟡 **In Progress**: supports only one of those capabilities, or support is announced, under development, or not yet generally available.
- 🔴 **Not Supported**: neither capability is publicly documented.

## Guidance

- Link only public, technical evidence: product documentation, release notes, security advisories, protocol specifications, or source code.
- Record the exact firmware/software version where support was introduced.
- Distinguish PQC support in operational protocols and management interfaces from PQC used solely to protect firmware updates.
- Note relevant constraints, such as hardware replacement requirements, maintenance-window needs, safety certification, or unsupported legacy models.
