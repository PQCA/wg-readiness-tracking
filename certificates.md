# PQC Readiness Tracker: Certificate Services

These pages track the state of Post-Quantum Cryptography (PQC) readiness for certificate authorities, CA software, and certificate lifecycle management services. This is a crowdsourced effort; please contribute by adding details about items you maintain or have reliable knowledge of.

**_AI assisted seed data for working out formatting and collected details. This is not complete or fully vetted._**

## Background

PQC certificate readiness involves two distinct layers that must not be conflated. This tracker covers TLS certificate issuance only; S/MIME and code signing are out of scope.

1. **CA software / private PKI** — tools that can issue certificates using ML-DSA or other NIST PQC algorithms for use within private or enterprise PKI environments.
2. **Publicly trusted Web PKI** — certificates issued by publicly trusted CAs for public TLS. This layer is **gated on root program acceptance**, which as of October 2026 has not been granted for ML-DSA in standard X.509 certificates. The CA/Browser Forum has not passed a ballot permitting ML-DSA in publicly trusted TLS certificates.
> ⚠️ **Root program dependency:** An entry marked 🟢 Ready means at least one NIST-standardized signature algorithm is supported for certificate issuance in a released version. It does not mean those certificates are trusted by browsers or publicly trusted root programs. Public Web PKI PQC authentication is contingent on:
> - CA/Browser Forum ballot approving ML-DSA in publicly trusted TLS certificates (no ballot passed as of October 2026)
> - Browser root program policies accepting PQC trust anchors (see `web-browsers.md`)
> - Sufficient CT log capacity to handle larger PQC certificate data volumes (flagged as a scaling concern in CA/Browser Forum discussions)

> ⚠️ **Merkle Tree Certificates (MTC):** The preferred path for public Web PKI PQC authentication is MTCs, currently in design at the IETF PLANTS working group. MTCs use ML-DSA cosignatures, short-lived certificates (~7 days), and have Certificate Transparency built in. Let's Encrypt, Cloudflare, and Chrome have all indicated MTC as their preferred approach. Production deployment is targeted for 2027. Entries below note which path (ML-DSA X.509 vs MTC) a CA is pursuing.

---

## CA Software (Self-Hosted / Private PKI)

| Software | Version | Status | Supported PQC Algorithms | Notes / Trackers |
| :--- | :--- | :--- | :--- | :--- |
| Boulder (Let's Encrypt ACME) | N/A | 🟡 In Progress | None yet (MTC path) | Let's Encrypt's ACME CA software. MTC staging environment targeted late 2026, production 2027. Also tracking ML-DSA X.509 via RFC 9881 and draft-ietf-tls-mldsa as a parallel path. Per [letsencrypt.org/2026/06/03/pq-certs](https://letsencrypt.org/2026/06/03/pq-certs). |
| CFSSL (Cloudflare) | v1.7.0 | 🟡 In Progress | ML-DSA | ML-DSA key generation and X.509 signing added via Go 1.27's `crypto/mldsa` package. Implements RFC 9881 key usage restrictions. Private keys marshalled as seed-only PKCS#8. Note: `multirootca` rejects ML-DSA roots at startup. No ML-KEM support. Per [cfssl v1.7.0 release](https://github.com/cloudflare/cfssl/releases/tag/v1.7.0). |
| Dogtag / Red Hat CS | >=11.10.1 | 🟡 In Progress | ML-KEM, ML-DSA | ML-KEM enrollment supported in `CRMFPopClient`; uses `POP_NONE` (no Proof of Possession) -- requests should be generated and submitted from a trusted, authenticated environment only. PoP support planned for a future release. ML-DSA appears in HSM compatibility tooling. Per [dogtagpki/pki commit 39aa595](https://github.com/dogtagpki/pki/commit/39aa5958523b6e5ea99cd2300c634e59b708912e). |
| EJBCA (Keyfactor) | >=9.1 | 🟢 Ready | ML-DSA; ML-KEM; SLH-DSA | ML-DSA and ML-KEM added in 9.1 (replaced earlier draft Dilithium/Kyber entries). SLH-DSA added in 9.3. Composite keys (classical + PQC) supported. PKCS#11 support for PQC HSM integration in development; vendor-specific. SCEP does not support PQC as of February 2026. Per [EJBCA PQC documentation](https://docs.keyfactor.com/ejbca/9.6/post-quantum-cryptography-keys-and-signatures). |
| HashiCorp Vault PKI | Enterprise >=1.19 | 🟡 In Progress | ML-DSA (Transit engine only, experimental) | Transit secrets engine adds ML-DSA sign/verify as experimental. PKI secrets engine PQC certificate issuance not yet confirmed as of October 2026. Per [Vault 1.19 release blog](https://www.hashicorp.com/blog/vault-enterprise-1-19-reduces-risk-encryption-updates-automated-root-rotation). |
| Microsoft AD CS | Windows Server 2025 + KB5087539 (May 2026) | 🟡 In Progress | ML-DSA | ML-DSA certificate issuance added for private PKI evaluation in May 2026 cumulative update. ML-KEM and broader ecosystem integration pending future updates. Per [Microsoft Learn: ML-DSA overview for AD CS](https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/ml-dsa-overview). |
| OpenXPKI | Enterprise (unreleased); Community TBD | 🟡 In Progress | ML-DSA | Basic PQC running in-lab using liboqs and oqsprovider. Enterprise Edition ships first; PKCS#11 3.2 PQC and HSM integration in progress. Community Edition timeline not committed; announcement targeted Q4 2026. PQ/T composite mechanism roadmap described as "not entirely foreseeable." Per [OpenXPKI users mailing list, Sept 2026](https://sourceforge.net/p/openxpki/mailman/message/59391814/). |
| Step CA (Smallstep) | N/A | 🔴 Not Supported | None (cert issuance) | No PQC certificate issuance supported. ML-KEM hybrid TLS key exchange (X25519MLKEM768) is available at the transport layer as of step-ca > 0.28.3 / step-cli > 0.28.6 but is out of scope for this tracker. ML-DSA deferred; Smallstep cites size and performance constraints and is waiting on NIST's follow-up signature standard. Per [Smallstep PQC blog](https://smallstep.com/blog/post-quantum-cryptography-at-smallstep/). |

---

## Public Certificate Authorities

> ⚠️ No publicly trusted CA can issue browser-trusted PQC TLS certificates as of October 2026. All entries below reflect private PKI capability, testing environments, or forward roadmap only.

| CA | Version | Status | Supported PQC Algorithms | Notes / Trackers |
| :--- | :--- | :--- | :--- | :--- |
| DigiCert | N/A | 🟡 In Progress | ML-DSA; SLH-DSA | ML-DSA certificates available now via DigiCert Private CA. SLH-DSA supported as a conservative alternative. DigiCert’s own TLS endpoints (digicert.com, one.digicert.com) already use x25519mlkem768. X9 PKI roots for all three ML-DSA variants in place. MTC prototypes in development. Public PQC certificates gated on CA/B Forum and browser root program acceptance -- DigiCert states this explicitly. Internal migration to ML-DSA-44 targeted by 2029. Per [DigiCert PQC migration plan](https://www.digicert.com/blog/digicert-post-quantum-infrastructure-migration-plan). |
| GlobalSign | ? | ? | ? | GlobalSign’s published PQC page uses pre-standardization algorithm names (Dilithium, Kyber) and contains apparent FIPS citation errors. No PQC product announcement confirmed against current documentation as of October 2026. Page appears stale; verify directly with GlobalSign before updating. Per [GlobalSign PQC page](https://www.globalsign.com/en/post-quantum-computing) (appears pre-2024). |
| Google Trust Services | N/A | 🟡 In Progress | None yet (MTC path) | Committed to MTCs as primary path. Staging environment targeted early 2027, production later in 2027. Per [Google Cloud PQC roadmap blog](https://cloud.google.com/blog/products/identity-security/pqc-in-plaintext-google-clouds-post-quantum-cryptography-roadmap). |
| IdenTrust | ? | ? | ? | No PQC documentation found as of October 2026. |
| Let’s Encrypt | N/A | 🟡 In Progress | None yet (MTC path) | Committed to MTCs as primary path. Staging environment targeted late 2026, production 2027. Also tracking ML-DSA X.509 (RFC 9881) as parallel path. Recommends operators enable X25519MLKEM768 hybrid TLS key exchange now. Per [letsencrypt.org/2026/06/03/pq-certs](https://letsencrypt.org/2026/06/03/pq-certs). |
| Sectigo | N/A | 🟡 In Progress | ML-DSA | "Private PQC" feature in Sectigo Certificate Manager (SCM) enables issuance and management of private-only PQC certificates for enterprise testing. Not publicly trusted. Existing Sectigo Private CA customers can request access via SCM. Per [Sectigo press release](https://www.sectigo.com/resource-library/private-pqc-in-sectigo-certificate-manager) and [Sectigo Private PQC brief](https://www.sectigo.com/uploads/resources/Private-PQC-brief-v3.pdf). |

---

## Cloud PKI & Certificate Lifecycle Managers

| Service | Version | Status | Supported PQC Algorithms | Notes / Trackers |
| :--- | :--- | :--- | :--- | :--- |
| AWS Certificate Manager (ACM) | ? | 🔴 Not Supported | None (cert issuance) | No PQC certificate issuance documented as of October 2026. ACM endpoints support ML-KEM hybrid TLS key exchange (X25519MLKEM768) as of April 2025 -- transport-layer only, not PQC certificate issuance. Note: AWS Private CA (a separate service) supports ML-DSA cert issuance. Per [AWS Security Blog, April 2025](https://aws.amazon.com/blogs/security/ml-kem-post-quantum-tls-now-supported-in-aws-kms-acm-and-secrets-manager/). |
| AWS Private CA | N/A | 🟡 In Progress | ML-DSA | ML-DSA certificate issuance supported for private PKI. Includes CA creation, end-entity cert issuance, CRL, and OCSP with ML-DSA. Available in all commercial, GovCloud, and China regions. Not publicly trusted. Per [AWS What's New, Nov 2025](https://aws.amazon.com/about-aws/whats-new/2025/11/aws-private-ca-post-quantum-digital-certificates/). |
| Azure Key Vault Certificates | ? | 🔴 Not Supported | None (cert issuance) | No PQC certificate issuance documented as of October 2026. Note: Azure Key Vault Premium supports AES-KW post-quantum resistant key wrapping (public preview as of Aug 2026) -- key management only, not PQC certificate issuance. Per [Microsoft Tech Community, Aug 2026](https://techcommunity.microsoft.com/blog/post-quantum-crypto-tech-blog/azure-key-vault-premium-and-aes-kw-post-quantum-resistant-key-wrapping-in-public/4544358). |
| Cloudflare | N/A | 🔴 Not Supported | None (cert issuance) | No PQC managed certificate issuance documented as of November 2026. Note: ML-KEM TLS key exchange and ML-DSA origin authentication are active but out of scope for this tracker. Per [Cloudflare SSL PQC docs](https://developers.cloudflare.com/ssl/post-quantum-cryptography/). |
| Cloudflare CA | ? | 🔴 Not Supported | ? | Cloudflare has indicated forthcoming CA capabilities. Details not yet documented publicly as of November 2026. |
| GCP Certificate Authority Service | ? | 🟡 In Progress | ML-DSA; SLH-DSA (roadmap) | Google Cloud roadmap targets CAS with ML-DSA and SLH-DSA certificate issuance in 2027. Not yet available as of November 2026. Per [Google Cloud PQC roadmap blog](https://cloud.google.com/blog/products/identity-security/pqc-in-plaintext-google-clouds-post-quantum-cryptography-roadmap). |
| GCP Certificate Manager | ? | 🔴 Not Supported | None (cert issuance) | No PQC certificate issuance documented as of November 2026. Google Trust Services MTC targeted 2028. Per [Google Cloud PQC roadmap blog](https://cloud.google.com/blog/products/identity-security/pqc-in-plaintext-google-clouds-post-quantum-cryptography-roadmap). |

---

Status: 🟢 Ready / 🟡 In Progress / 🔴 Not Supported

### Status Definitions

- 🟢 **Ready**: At least one NIST-standardized signature algorithm (e.g. ML-DSA, SLH-DSA) supported for certificate issuance in a released version.
- 🟡 **In Progress**: PQC support is experimental, lab-only, unreleased, or roadmap only; or only TLS key exchange (ML-KEM) is present with no PQC certificate issuance.
- 🔴 **Not Supported**: No PQC support documented.
---

## How to Contribute

1. Fork this repo.
2. Update the relevant table with new information or corrections.
3. Submit a Pull Request with the tag `[PQC-Readiness]`.
---

## Guidance

- All linked sources should point to official technical documentation, changelogs, or release notes. Press releases are acceptable only when accompanied by a link to the underlying technical source.
- ML-KEM TLS key exchange (e.g. X25519MLKEM768) is out of scope for status scoring in this tracker. Transport-layer PQC does not elevate an entry's status. Track TLS and network-layer PQC readiness in `network.md` or a dedicated TLS tracker.
- **Distinguish private PKI from public Web PKI.** A CA software product that can issue ML-DSA certificates for private use is not the same as a publicly trusted CA that can issue browser-trusted PQC certificates. These are different capabilities with different prerequisites.
- Public Web PKI PQC readiness is gated on CA/Browser Forum root program acceptance and browser root program policy. Track browser root program status in `web-browsers.md`, not here.
- Note whether PQC support is experimental, preview, or production-ready.
- Note which path the CA is pursuing: ML-DSA X.509 (RFC 9881), Merkle Tree Certificates (MTC via IETF PLANTS), or both. These are architecturally different approaches.
- CT log capacity is a known open issue for ML-DSA X.509 at scale; note this when relevant.
- The [PKIC PQCCM](https://pkic.org/wg/pqc/pqccm/) is archived and no longer maintained; use it for product discovery only, then verify against current vendor documentation. PQC capabilities will be tracked going forward via the [PKIC PQC Maturity Model](https://pkic.org/wg/pqc/pqcmm/).
