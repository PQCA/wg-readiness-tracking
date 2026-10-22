# PQC Readiness Tracker: Web Browsers

This page tracks the state of Post-Quantum Cryptography (PQC) readiness for major web browsers, focusing on their ability to support PQC algorithms in TLS connections.

These trackers are a crowdsourced effort; please contribute by updating the status of browsers you maintain or use.

## Major Web Browsers

| Browser | Version | Status | Platform | Supported Algorithms | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Google Chrome | >=131 | 🟡 In Progress | Windows, macOS, Linux, Android, iOS | ML-KEM | Chrome 124 enabled the pre-standard X25519Kyber768Draft00 hybrid by default; Chrome 131 replaced it with the standardized X25519MLKEM768 hybrid (codepoint 0x11EC). Uses BoringSSL. No PQC signature (ML-DSA) support in TLS yet; Chrome has no immediate plan to accept PQC X.509 certificates and is instead experimenting with Merkle Tree Certificates (MTCs) with Cloudflare, with a Chrome Quantum-resistant Root Store targeted for Q3 2027. The draft Chrome Quantum-resistant Root Program Policy v0.3.0 (August 14, 2026) requires at least 2 cosignatures per standalone certificate (one from the MTC CA operator, one from an independent mirroring cosigner) using ML-DSA-44. https://security.googleblog.com/2024/09/a-new-path-for-kyber-on-web.html https://blog.google/security/cultivating-a-robust-and-efficient-quantum-safe-https/ https://googlechrome.github.io/chromerootprogram/cqrp/draft-policy/ |
| Microsoft Edge | >=131 | 🟡 In Progress | Windows, macOS, Linux, Android, iOS | ML-KEM | Based on Chromium, follows Chrome's PQC implementation timeline. X25519MLKEM768 hybrid key exchange enabled by default in version 131. No PQC signature support yet. https://developers.cloudflare.com/ssl/post-quantum-cryptography/pqc-support/ |
| Brave | >=1.73.86 | 🟡 In Progress | Windows, macOS, Linux, Android, iOS | ML-KEM | Based on Chromium 131, X25519MLKEM768 hybrid key exchange enabled by default. Follows upstream Chromium PQC implementation. No PQC signature support yet. https://developers.cloudflare.com/ssl/post-quantum-cryptography/pqc-support/ |
| Opera | >=116 | 🟡 In Progress | Windows, macOS, Linux, Android | ML-KEM | Based on Chromium 131, X25519MLKEM768 hybrid key exchange enabled by default following upstream implementation. No PQC signature support yet. https://developers.cloudflare.com/ssl/post-quantum-cryptography/pqc-support/ |
| Mozilla Firefox | >=132 (Desktop), >=145 (Android) | 🟡 In Progress | Windows, macOS, Linux, Android | ML-KEM | Uses NSS. Firefox 132 added X25519MLKEM768 (mlkem768x25519) for TLS 1.3 on desktop; Firefox 135 extended it to HTTP/3 (QUIC); Firefox 145 added it on Android for TLS 1.3 and HTTP/3. No PQC signature support yet. https://www.firefox.com/en-US/firefox/132.0/releasenotes/ https://www.firefox.com/en-US/firefox/135.0/releasenotes/ https://www.firefox.com/firefox/android/145.0/releasenotes/ |
| Apple Safari | >=26 | 🟡 In Progress | macOS, iOS, iPadOS, visionOS | ML-KEM | In iOS 26, iPadOS 26, macOS Tahoe 26 and visionOS 26, TLS 1.3 connections advertise X25519MLKEM768 by default (URLSession and Network APIs, used by Safari). No PQC signature support yet; the Apple Root Program announced its PQC policy position on September 21, 2026, adopting MTCs for TLS server authentication (7-day validity cap, 3 cosignatures: ML-DSA and ECDSA from the issuing operator plus ML-DSA from a separate mirroring operator) and expects to publish a draft MTC policy by the end of October 2026. https://support.apple.com/guide/security/sec100a75d12/web https://support.apple.com/en-us/122756 https://groups.google.com/a/chromium.org/g/ct-policy/c/QGZw2ADMXvk/m/pR3A5uRZCAAJ |

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
* All linked information should point to an official repository or technical documentation. If you provide a link to a press releases or product page, you will be asked to provide a different link.
* For browsers, please include version numbers where PQC support was introduced.
* Focus on TLS/HTTPS connection security rather than other cryptographic features.
