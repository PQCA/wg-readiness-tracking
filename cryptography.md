# PQC Readiness Tracker: Cryptography Libraries and Tools

This page tracks the state of Post-Quantum Cryptography (PQC) readiness for common cryptography libraries.

These trackers are a crowdsourced effort; please contribute by updating the status of packages you maintain or use.

## Common Cryptography Libraries

*** Seed data for working out formatting and collected details. This is not complete or fully vetted. ***

| Package Name | Version| Status | Language | Supported Algorithms | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Example Library | 1.0 | 🔴 Not Started | C, Go | ML-KEM,  ML-DSA, Other (LMS, SLH-DSA, Falcon) | Link to issue/PR |
| BoringSSL | [>=20250818](https://github.com/google/boringssl/releases/tag/0.20250818.0) | 🟢 Ready | C/C++ | ML-KEM, ML-DSA, SLH-DSA, X-Wing | https://commondatastorage.googleapis.com/chromium-boringssl-docs/mlkem.h.html. No support for ML-KEM-512.  |
| aws-lc |  | 🟢 Ready | C/C++ | ML-KEM, ML-DSA|   |
| bssl-crypto | ? | 🟢 Ready | Rust | ? | |
| Botan | >=3.6.0 | 🟢 Ready | C++ | ML-KEM, ML-DSA, SLH-DSA, HSS/LMS, XMSS, FrodoKEM, McEliece | |
| Bouncy Castle	| Java >= 1.79, C# >= 2.5.0 |	🟢 Ready | Java, C#	| ML-KEM, ML-DSA, SLH-DSA	| Full support for finalized NIST standards was added in these versions (released late 2024). |
| Conscrypt| [Commit 4b9f688](https://github.com/google/conscrypt/commit/4b9f688b241f73a89ba1eb8871b302062c1790ff)| 🟡 In Progress | Java | ML-DSA, SLH-DSA | No direct support of ML-KEM but via HPKE. Support of SLH-DSA-SHA2-128S. Supports ML-DSA-44/65/87|
| JDK (JCA) | >=24 | 🟢 Ready | Java | ML-KEM | ML-KEM via [JEP 496](https://openjdk.org/jeps/496), ML-DSA via [JEP 497](https://openjdk.org/jeps/497) |
| JDK (TLS 1.3) | [>=27](https://openjdk.org/projects/jdk/27/) | 🟡 In Progress | Java | ML-KEM (hybrid ECDHE) | TLS 1.3 hybrid key exchange via [JEP 527](https://openjdk.org/jeps/527). Targeted for JDK 27 release. |
| Crypto++	| N/A	| 🔴 Not Supported | C++ | None | A community fork called CryptoPP-Modern has added experimental support |
| GnuTLS | N/A | 🔴 Not Supported | C | None | No native PQC support yet. Experimental support was available via liboqs in earlier versions but not maintained |
| Go crypto | [>=1.24](https://pkg.go.dev/crypto/mlkem@go1.24) | 🟡 In Progress | Go | ML-KEM, ML-DSA | PQC roadmap at https://github.com/golang/go/issues/64537. ML-DSA planned for go [1.27](https://github.com/golang/go/issues/77626). No support for ML-KEM-512. No plan for SLH-DSA but see [go-slh-dsa](https://github.com/trailofbits/go-slh-dsa)|
| IDEMIA Sphere Cryptographic Library | 1.0.0 | 🟢 Ready | C, Python, Java | ML-KEM, ML-DSA, LMS, SLH-DSA | FIPS CAVP certified https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/details?product=19694 |
| libsodium	| N/A |	🔴 Not Supported | C | None | Historically focused on well-established classical primitives and has not yet integrated native PQC algorithms into the core library |
| mbedTLS | - | 🔴 Not Started | C | None | No support, yet. Crypto API [Extension PQC 1.4](https://arm-software.github.io/psa-api/crypto/1.4/ext-pqc/) available.|
| noble cryptography | [0.6.1](https://github.com/paulmillr/noble-post-quantum/releases/tag/0.6.1) | 🟢 Ready | TypeScript / JS  | ML-KEM, ML-DSA, SLH-DSA, HSS/LMS, Falcon (Round 3) |  Support for hybids (Concrete, XWing, KitchenSink)|
| NSS (Network Security Services) | N/A | 🔴 Not Supported | C | None | Used by Firefox and other Mozilla products. No native PQC support yet |
| OpenSSL | [>=3.5](https://openssl-library.org/post/2025-04-08-openssl-35-final-release/) | 🟢 Ready | C | | Native support for ML-KEM-512/768/1024, ML-DSA and SLH-DSA was introduced in [OpenSSL 3.5](https://openssl.foundation/news/the-features-of-3-5-post-quantum-cryptography). Older versions require the third-party Open Quantum Safe (OQS) provider |
| PyCa/cryptography |	N/A |	🔴 Not Supported | Python | None | The standard Python cryptography package does not yet have native support. Users typically use wrappers like pyoqs or wolfcrypt-py |
| PyCa/cryptography (w/ external libraries) |	>=47.0.0 |	🟢 Ready | Python | ML-KEM, ML-DSA | Initial support in [47.0.0](https://cryptography.io/en/latest/changelog/#v47-0-0) only when compiled against AWS-LC or BoringSSL. Support when built against OpenSSL and in their official PyPI wheels [only >=48.0.0](https://cryptography.io/en/latest/changelog/#v48-0-0) |
| pycryptodome | N/A | 🔴 Not Supported | Python | None | Popular Python cryptography library and PyCrypto fork. No native PQC support yet |
| pyoqs (liboqs Python) | [>=0.11.0](https://github.com/open-quantum-safe/liboqs-python) | 🟢 Ready | Python | ML-KEM, ML-DSA, SLH-DSA, BIKE, Classic McEliece, HQC, Kyber, Falcon | Python wrapper for liboqs providing comprehensive PQC algorithm support. Part of Open Quantum Safe project. https://github.com/open-quantum-safe/liboqs-python |
| ring |	N/A |	🔴 Not Supported	| Rust |	None	| The ring crate does not support ML-KEM. Rust developers often use ml-kem (from the RustCrypto project) or aws-lc-rs for PQC support |
| RustCrypto ml-dsa | [>=0.1.0](https://github.com/RustCrypto/signatures) | 🟢 Ready | Rust | ML-DSA | Pure Rust implementation of ML-DSA (Dilithium). Part of RustCrypto project. https://crates.io/crates/ml-dsa |
| RustCrypto ml-kem | [>=0.1.0](https://github.com/RustCrypto/KEMs) | 🟢 Ready | Rust | ML-KEM | Pure Rust implementation of ML-KEM (Kyber). Part of RustCrypto project. https://crates.io/crates/ml-kem |
| ring |	N/A |	🔴 Not Supported	| Rust |	None	| The ring crate does not support ML-KEM. Rust developers often use ml-kem (from the RustCrypto project) or aws-lc-rs for PQC support |
| rustls | N/A | 🔴 Not Supported | Rust | None | Modern TLS library for Rust. No native PQC support yet, though underlying crypto provider (ring/aws-lc-rs) support would be needed first |
| s2n-tls | N/A | 🔴 Not Supported | C | None | AWS's TLS implementation. No native PQC support yet |
| wolfcrypt-py | [>=5.7.0](https://github.com/wolfSSL/wolfcrypt-py) | 🟢 Ready | Python | ML-KEM, ML-DSA, SLH-DSA, LMS/HSS | Python wrapper for wolfSSL's wolfCrypt library. Provides PQC support through underlying wolfSSL implementation |
| wolfSSL	| >=v5.8.0  |	🟢 Ready | C | ML-KEM, ML-DSA, SLH-DSA, LMS/HSS, XMSS/XMSS^MT | Initial support for PQC was introduced in v5.0.0 using liboqs. Native PQC implementations were introduced in v5.7.0, and support for liboqs was deprecated in [February 2025](https://www.wolfssl.com/deprecation-notice-liboqs-integration/)	|


Status: 🟢 Ready / 🟡 In Progress / 🔴 Not Started

## How to Contribute
1. Fork this repo.
2. Update the table above with new information or edits.
3. Submit a Pull Request with the tag `[PQC-Readiness]`.

## Guidance
* All linked information should point to an official repository or technical documentation. If you provide a link to a press releases or product page, you will be asked to provide a different link.
3. Update the table above with current information.
4. Submit a Pull Request with the tag `[PQC-Readiness]`.
