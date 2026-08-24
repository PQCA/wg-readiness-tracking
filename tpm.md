# PQC Readiness Tracker: Trusted Platform Modules (TPMs)

This page tracks the state of Post-Quantum Cryptography (PQC) readiness 
for Trusted Platform Modules (TPMs).

These trackers are a crowdsourced effort; please contribute by adding 
details about items you maintain or have reliable knowledge of.

## Background

The [TCG PC Client Platform TPM Profile (PTP) 1.07](https://trustedcomputinggroup.org/wp-content/uploads/PC-Client-Specific-Platform-TPM-Profile-for-TPM-2p0-v1p07_Pub.pdf) 
defines the baseline for PQC-ready TPMs. ML-KEM and ML-DSA are mandatory 
as of PTP 1.07. TCG has defined two transition designations:

- **TCG PQC-ready TPM** — implements PTP 1.07
- **TCG PQC-upgradable TPM** — does not currently support PTP 1.07 but 
  can be upgraded via firmware

TCG plans to certify TPMs against PTP 1.07. Details on the certification 
program are forthcoming. See [TCG guidance on PQC-ready TPMs](https://trustedcomputinggroup.org).

## Trusted Platform Modules

**_Seed data — not complete or fully vetted._**

| Vendor / Model | Firmware Version | PQC Status | TCG Designation | Supported PQC Algorithms | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Example TPM | 1.0 | 🔴 Not Supported | N/A | None | Link to source |