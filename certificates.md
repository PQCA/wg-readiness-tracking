# PQC Readiness Tracker: Certificate Services

These pages track the state of Post-Quantum Cryptography (PQC) readiness for certificate authorities, CA software, and certificate lifecycle management services. This is a crowdsourced effort; please contribute by adding details about items you maintain or have reliable knowledge of.

**_AI assisted seed data for working out formatting and collected details. This is not complete or fully vetted._**

## Background

PQC certificate readiness involves two distinct layers that must not be conflated:

1. **CA software / private PKI** — tools that can issue certificates using ML-DSA or other NIST PQC algorithms for use within private or enterprise PKI environments.
2. **Publicly trusted Web PKI** — certificates issued by publicly trusted CAs for public TLS. This layer is **gated on root program acceptance**, which as of October 2026 has not been granted for ML-DSA in standard X.509 certificates. The CA/Browser Forum has not passed a ballot permitting ML-DSA in publicly trusted TLS certificates.

> ⚠️ **Root program dependency:** An entry marked 🟢 Ready for CA software means it can issue PQC certificates for private PKI. It does not mean those certificates are trusted by browsers or publicly trusted root programs. Public Web PKI PQC authentication is contingent on:
> - CA/Browser Forum ballot approving ML-DSA in publicly trusted TLS certificates (no ballot passed as of October 2026)
> - Browser root program policies accepting PQC trust anchors (see `web-browsers.md`)
> - Sufficient CT log capacity to handle larger PQC certificate data volumes (flagged as a scaling concern in CA/Browser Forum discussions)

> ⚠️ **Merkle Tree Certificates (MTC):** The preferred path for public Web PKI PQC authentication is MTCs, currently in design at the IETF PLANTS working group. MTCs use ML-DSA cosignatures, short-lived certificates (~7 days), and have Certificate Transparency built in. Let's Encrypt, Cloudflare, and Chrome have all indicated MTC as their preferred approach. Production deployment is targeted for 2027. Entries below note which path (ML-DSA X.509 vs MTC) a CA is pursuing.

---

## CA Software (Self-Hosted / Private PKI)

| Software | Version | Status | Supported PQC Algorithms | Notes / Trackers |
| :--- | :--- | :--- | :--- | :--- |
| EJBCA (Keyfactor) | >=9.1 | 🟢 Ready | ML-DSA; ML-KEM| ML-DSA and ML-KEM added in 9.1 (replaced earlier draft Dilithium/Kyber entries). Composite keys (classical + PQC) supported. PKCS#11 support for PQC HSM integration in development; vendor-specific. SCEP does not support PQC as of February 2026. Per [EJBCA PQC documentation](https://docs.keyfactor.com/ejbca/9.6/post-quantum-cryptography-keys-and-signatures). |
| Microsoft AD CS | Windows Server 2025 + KB5087539 (May 2026) | 🟡 In Progress | ML-DSA | ML-DSA certificate issuance added for private PKI evaluation in May 2026 cumulative update. ML-KEM and broader ecosystem integration pending future updates. Per [directaccess.richardhicks.com](https://directaccess.richardhicks.com/category/security-2). |
| HashiCorp Vault PKI | Enterprise >=1.19 | 🟡 In Progress | ML-DSA (Transit engine only, experimental) | Transit secrets engine adds ML-DSA sign/verify as experimental. PKI secrets engine PQC certificate issuance not yet confirmed as of October 2026. Per [Vault 1.19 release blog](https://www.hashicorp.com/blog/vault-enterprise-1-19-reduces-risk-encryption-updates-automated-root-rotation). |
| Boulder (Let's Encrypt ACME) | N/A | 🟡 In Progress | None yet (MTC path) | Let's Encrypt's ACME CA software. MTC staging environment targeted late 2026, production 2027. Also tracking ML-DSA X.509 via RFC 9881 and draft-ietf-tls-mldsa as a parallel path. Per [letsencrypt.org/2026/06/03/pq-certs](https://letsencrypt.org/2026/06/03/pq-certs). |
| Step CA (Smallstep) | step-ca >=0.28.3 / step-cli >=0.28.6 | 🟡 In Progress | X25519MLKEM768 (hybrid TLS key exchange only) | ML-KEM hybrid key exchange supported at the TLS layer; requires `GODEBUG=tlsmlkem=1` to enable (flag expected to be removed in a future Go update). ML-DSA deferred -- Smallstep cites size and performance constraints and is waiting on NIST's follow-up signature standard. Hybrid X.509 certificate issuance and hybrid CA on roadmap with no committed dates. Per [Smallstep PQC blog](https://smallstep.com/blog/post-quantum-cryptography-at-smallstep/). |
| Dogtag / Red Hat CS | >=11.10.1 | 🟡 In Progress | ML-KEM, ML-DSA | ML-KEM enrollment supported in `CRMFPopClient`; uses `POP_NONE` (no Proof of Possession) -- requests should be generated and submitted from a trusted, authenticated environment only. PoP support planned for a future release. ML-DSA appears in HSM compatibility tooling. Per [dogtagpki/pki commit 39aa595](https://github.com/dogtagpki/pki/commit/39aa5958523b6e5ea99cd2300c634e59b708912e). |
| OpenXPKI | Enterprise (unreleased); Community TBD | 🟡 In Progress | ML-DSA | Basic PQC running in-lab using liboqs and oqsprovider. Enterprise Edition ships first; PKCS#11 3.2 PQC and HSM integration in progress. Community Edition timeline not committed; announcement targeted Q4 2026. PQ/T composite mechanism roadmap described as "not entirely foreseeable." Per [OpenXPKI users mailing list, Sept 2026](https://sourceforge.net/p/openxpki/mailman/message/59391814/). |
| CFSSL (Cloudflare) | v1.7.0 | 🟡 In Progress | ML-DSA | ML-DSA key generation and X.509 signing added via Go 1.27's `crypto/mldsa` package. Implements RFC 9881 key usage restrictions. Private keys marshalled as seed-only PKCS#8. Note: `multirootca` rejects ML-DSA roots at startup. No ML-KEM support. Per [cfssl v1.7.0 release](https://github.com/cloudflare/cfssl/releases/tag/v1.7.0). |

---

## Public Certificate Authorities

> ⚠️ No publicly trusted CA can issue browser-trusted PQC TLS certificates as of October 2026. All entries below reflect private PKI capability, testing environments, or forward roadmap only.

| CA | Version | Status | Supported PQC Algorithms | Notes / Trackers |
| :--- | :--- | :--- | :--- | :--- |
| Let's Encrypt | N/A | 🟡 In Progress | None yet (MTC path) | Committed to MTCs as primary path. Staging environment targeted late 2026, production 2027. Also tracking ML-DSA X.509 (RFC 9881) as parallel path. Recommends operators enable X25519MLKEM768 hybrid TLS key exchange now. Per [letsencrypt.org/2026/06/03/pq-certs](https://letsencrypt.org/2026/06/03/pq-certs). |
| Sectigo | N/A | 🟡 In Progress | ML-DSA | "Private PQC" feature in Sectigo Certificate Manager (SCM) enables issuance and management of private-only PQC certificates for enterprise testing. Not publicly trusted. Existing Sectigo Private CA customers can request access via SCM. Per [Sectigo press release](https://www.sectigo.com/resource-library/private-pqc-in-sectigo-certificate-manager) and [Sectigo Private PQC brief](https://www.sectigo.com/uploads/resources/Private-PQC-brief-v3.pdf). |
| Entrust | CA Gateway >=3.7.0 | 🟡 In Progress | ML-DSA, ML-KEM | CA Gateway 3.7.0 adds PQC algorithm support when integrating an Entrust CA. Private PKI use only. Per [CA Gateway 3.7.0 release notes](https://api.managed.entrust.com/cagw/3.7/New-features-for-3.7.0.html). |
| DigiCert | N/A | 🟡 In Progress | ML-DSA; SLH-DSA (Private CA); x25519mlkem768 (TLS endpoints) | ML-DSA certificates available now via DigiCert Private CA. SLH-DSA supported as a conservative alternative. DigiCert’s own TLS endpoints (digicert.com, one.digicert.com) already use x25519mlkem768. X9 PKI roots for all three ML-DSA variants in place. MTC prototypes in development. Public PQC certificates gated on CA/B Forum and browser root program acceptance -- DigiCert states this explicitly. Internal migration to ML-DSA-44 targeted by 2029. Per [DigiCert PQC migration plan](https://www.digicert.com/blog/digicert-post-quantum-infrastructure-migration-plan). |
| GlobalSign | ? | ? | ? | GlobalSign's published PQC page uses pre-standardization algorithm names (Dilithium, Kyber) and contains apparent FIPS citation errors. No PQC product announcement confirmed against current documentation as of October 2026. Page appears stale; verify directly with GlobalSign before updating. Per [GlobalSign PQC page](https://www.globalsign.com/en/post-quantum-computing) (appears pre-2024). |
| IdenTrust | ? | ? | ? | No PQC documentation found as of October 2026. |

---

## Cloud Certificate Managers

| Service | Version | Status | Supported PQC Algorithms | Notes / Trackers |
| :--- | :--- | :--- | :--- | :--- |
| AWS Certificate Manager (ACM) | ? | 🔴 Not Supported | None (cert issuance) | No PQC certificate issuance documented as of October 2026. ACM endpoints support ML-KEM hybrid TLS key exchange (X25519MLKEM768) as of April 2025 -- transport-layer only, not PQC certificate issuance. Note: AWS Private CA (a separate service) supports ML-DSA cert issuance. Per [AWS Security Blog, April 2025](https://aws.amazon.com/blogs/security/ml-kem-post-quantum-tls-now-supported-in-aws-kms-acm-and-secrets-manager/). |
| Azure Key Vault Certificates | ? | 🔴 Not Supported | None (cert issuance) | No PQC certificate issuance documented as of October 2026. Note: Azure Key Vault Premium supports AES-KW post-quantum resistant key wrapping (public preview as of Aug 2026) -- key management only, not PQC certificate issuance. Per [Microsoft Tech Community, Aug 2026](https://techcommunity.microsoft.com/blog/post-quantum-crypto-tech-blog/azure-key-vault-premium-and-aes-kw-post-quantum-resistant-key-wrapping-in-public/4544358). |
| GCP Certificate Manager | ? | 🔴 Not Supported | None (cert issuance) | No PQC certificate issuance documented as of October 2026. Google Cloud roadmap targets Private CA (Certificate Authority Service) with ML-DSA/SLH-DSA in 2027, Google Trust Services MTC in 2028. Cloud KMS already supports ML-KEM, ML-DSA, and SLH-DSA as signing/encryption keys (GA). Load balancers support X25519MLKEM768 TLS opt-in. Per [Google Cloud PQC roadmap blog](https://cloud.google.com/blog/products/identity-security/pqc-in-plaintext-google-clouds-post-quantum-cryptography-roadmap). |
| Cloudflare SSL/TLS | N/A | 🟡 In Progress | X25519MLKEM768; ML-DSA | Hybrid ML-KEM (X25519MLKEM768) supported for visitor-to-Cloudflare TLS 1.3 since Oct 2022; origin-to-Cloudflare hybrid key exchange also available. ML-DSA deployed for Cloudflare-to-origin authentication only; visitor-facing ML-DSA authentication still in development. No PQC managed certificate issuance documented as of October 2026. Full PQC across product suite targeted 2029. Per [Cloudflare SSL PQC docs](https://developers.cloudflare.com/ssl/post-quantum-cryptography/). |

---

Status: 🟢 Ready / 🟡 In Progress / 🔴 Not Supported

### Status Definitions

- 🟢 **Ready**: at least 1 NIST-standardized key exchange algorithm (e.g. ML-KEM) AND at least 1 NIST-standardized signature algorithm (e.g. ML-DSA) are supported for certificate issuance.
- 🟡 **In Progress**: only one of the two is supported, or support is experimental / private PKI only / roadmap.
- 🔴 **Not Supported**: neither is supported.

---

## How to Contribute

1. Fork this repo.
2. Update the relevant table with new information or corrections.
3. Submit a Pull Request with the tag `[PQC-Readiness]`.

---

## Guidance

- All linked sources should point to official technical documentation, changelogs, or release notes. Press releases are acceptable only when accompanied by a link to the underlying technical source.
- **Distinguish private PKI from public Web PKI.** A CA software product that can issue ML-DSA certificates for private use is not the same as a publicly trusted CA that can issue browser-trusted PQC certificates. These are different capabilities with different prerequisites.
- Public Web PKI PQC readiness is gated on CA/Browser Forum root program acceptance and browser root program policy. Track browser root program status in `web-browsers.md`, not here.
- Note whether PQC support is experimental, preview, or production-ready.
- Note which path the CA is pursuing: ML-DSA X.509 (RFC 9881), Merkle Tree Certificates (MTC via IETF PLANTS), or both. These are architecturally different approaches.
- CT log capacity is a known open issue for ML-DSA X.509 at scale; note this when relevant.
