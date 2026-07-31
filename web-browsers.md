# PQC Readiness Tracker: Web Browsers

This page tracks the state of Post-Quantum Cryptography (PQC) readiness for major web browsers, focusing on their ability to support PQC algorithms in TLS connections.

These trackers are a crowdsourced effort; please contribute by updating the status of browsers you maintain or use.

## Major Web Browsers

| Browser | Version | Status | Platform | Supported Algorithms | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Google Chrome | >=131 | 🟢 Ready | Windows, macOS, Linux, Android, iOS | ML-KEM (Kyber) | Chrome enabled ML-KEM-768 (X25519Kyber768) hybrid key exchange by default starting in Chrome 131. Uses BoringSSL which supports ML-KEM. https://blog.chromium.org/2024/09/building-quantum-resistant-encryption.html |
| Microsoft Edge | >=131 | 🟢 Ready | Windows, macOS, Linux, Android, iOS | ML-KEM (Kyber) | Based on Chromium, follows Chrome's PQC implementation timeline. Enabled ML-KEM-768 hybrid key exchange in version 131. |
| Brave | >=1.73 | 🟢 Ready | Windows, macOS, Linux, Android, iOS | ML-KEM (Kyber) | Based on Chromium, enabled ML-KEM-768 hybrid key exchange. Follows upstream Chromium PQC implementation. |
| Opera | >=117 | 🟢 Ready | Windows, macOS, Linux, Android | ML-KEM (Kyber) | Based on Chromium, supports ML-KEM-768 hybrid key exchange following upstream implementation. |
| Mozilla Firefox | N/A | 🔴 Not Supported | Windows, macOS, Linux, Android, iOS | None | Firefox does not yet have native PQC support in TLS. Uses NSS for cryptography which lacks PQC implementation. Tracking in https://bugzilla.mozilla.org/show_bug.cgi?id=1857217 |
| Apple Safari | N/A | 🔴 Not Supported | macOS, iOS, iPadOS | None | Safari does not yet have announced PQC support in TLS. Apple has not publicly disclosed PQC implementation timeline. |

Status: 🟢 Ready / 🟡 In Progress / 🔴 Not Supported

## How to Contribute
1. Fork this repo.
2. Update the table above with new information or edits.
3. Submit a Pull Request with the tag `[PQC-Readiness]`.

## Guidance
* All linked information should point to an official repository or technical documentation. If you provide a link to a press releases or product page, you will be asked to provide a different link.
* For browsers, please include version numbers where PQC support was introduced.
* Focus on TLS/HTTPS connection security rather than other cryptographic features.
