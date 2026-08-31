# PQC Tracking

The Post-Quantum Cryptography Alliance PQC Readiness Tracking Working Group is a community
driven effort to collect, verify and publish information about devices and software that need
to be updated to remain secure when post-quantum computers can factor (break) classical
asymmetric cryptography.

## WG Details

* Working Group Mailing List: https://lists.pqca.org/g/wg-readiness-tracking 
* GitHub Repository: https://github.com/PQCA/wg-readiness-tracking 
* Meeting Cadence: Every 2 weeks @ 9am US/Pacific time, beginning May 21, 2026 [meeting link](https://zoom-lfx.platform.linuxfoundation.org/meeting/92180236021?password=b0389cf7-46b4-4b12-8960-743736597cff)

---
## Trackers

* [Cryptographic Libraries](cryptography.md) - Tracking PQC readiness for cryptography libraries and tools
* [HSMs](hsm.md) - Hardware Security Modules
* [Web Browsers](web-browsers.md) - Tracking PQC support in major web browsers
* [TPMs](tpm.md) - Trusted Platform Modules

## Other Data Sources

* [Cloudflare PQC Tracker](https://developers.cloudflare.com/ssl/post-quantum-cryptography/pqc-support/)
* [PKI Consortium Tracker](https://pkic.org/wg/pqc/pqccm/) - Outdated, but potentially useful

## General Guidance

1. Focus first on Harvest Now Decrypt Later (HNDL) / Store Now Decrypt Later (SNDL) first by protecting key exchanges.
2. As Post-quantum secure key encapsulation is deployed, start working on signature algorithm updates. 
3. Lead with discovery and inventory. Without basic cryptographic hygiene, you cannot make fully informed decisions about where to focus.
4. As your inventory improves work on cryptographic agility. To the extent possible use libraries like [Tink](https://developers.google.com/tink) that support multiple keysets and can substantially de-risk and ease transitions.
6. For use cases that rely on TLS for transport security and signing, if you cannot move to TLS 1.3 with downgrade protections, you do not have a reliable path to PQC. If you rely on the WebPKI for public trust (use public CAs), plan to move to [Merkle Tree Certificates](https://datatracker.ietf.org/doc/draft-ietf-plants-merkle-tree-certs/). For private PKIs, plan to move to ML-DSA signatures in X.509.

CISA offers a good general [PQC risk management framework](https://www.cisa.gov/topics/risk-management/quantum)

## AI Use Guidelines

It is acceptable to use AI tools to help gather information, but contributors must self-review their changes before opening a PR.
Contributors are also encouraged to disclose any AI tools used, to help maintain transparency.

## Bootstrapping

To make it easy to contribute and consume readiness information, Markdown tables are used based
on the [Proposed tracking template](tracking-template.md).

The initial focus of the working group is to refine the format and processes for vetting and
approving information using the [Cryptographic Library tracker](cryptography.md)
