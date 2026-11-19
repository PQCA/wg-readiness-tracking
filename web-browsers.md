# PQC Readiness Tracker: Web Browsers

This page tracks the state of Post-Quantum Cryptography (PQC) readiness for major web browsers, focusing on their ability to support PQC algorithms in TLS connections.

These trackers are a crowdsourced effort; please contribute by updating the status of browsers you maintain or use.

## Major Web Browsers

| Browser | Engine / TLS Stack | Minimum PQC Version | TLS / QUIC Key Exchange Status | WebPKI Cert Auth Status | Supported PQC Algorithms | Notes / Documentation |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Apple Safari | WebKit (`Network.framework` / corecrypto) | Safari 26+ (macOS Tahoe 26, iOS 26, iPadOS 26) | 🟢 Ready | 🔴 Not Supported | KEM: `X25519MLKEM768` (`0x11EC`) | Enabled by default for TLS 1.3 and QUIC connections starting in Safari 26 / OS 26 releases via Apple's system `Network.framework` TLS stack. ([Apple Platform Security](https://support.apple.com/guide/security/welcome/web)) |
| Brave | Blink / BoringSSL *(Desktop & Android)*; WebKit *(iOS)* | v1.73+ (Chromium 131+; iOS requires iOS 26+) | 🟢 Ready | 🟡 In Progress *(Inherits Chromium MTC support)* | KEM: `X25519MLKEM768` (`0x11EC`) | Inherits Chromium 131+ BoringSSL default support for `X25519MLKEM768` in TLS 1.3 and QUIC on Desktop and Android. ([Chromium PQC Blog](https://blog.chromium.org/2024/05/advancing-our-amazing-bet-on-asymmetric.html)) |
| Google Chrome | Blink / BoringSSL *(Desktop & Android)*; WebKit *(iOS)* | Chrome 131+ (Desktop & Android; iOS requires iOS 26+) | 🟢 Ready | 🟡 In Progress *(Merkle Tree Certificates pilot)* | KEM: `X25519MLKEM768` (`0x11EC`)<br>WebPKI (Experimental): Merkle Tree Certificates (`MTC` / `ML-DSA`) | `X25519MLKEM768` (FIPS 203) replaced the pre-standard `X25519Kyber768Draft00` in Chrome 131 (Nov 2024) and is enabled by default in TLS 1.3 and HTTP/3 (QUIC). Chrome is actively piloting Merkle Tree Certificates (IETF PLANTS) for quantum-safe WebPKI authentication. ([Chrome Platform Status #5085386357538816](https://chromestatus.com/feature/5085386357538816), [Google Security Blog WebPKI Roadmap](https://security.googleblog.com/2026/03/sustaining-digital-trust-journey-toward.html)) |
| Microsoft Edge | Blink / BoringSSL *(Desktop & Android)*; WebKit *(iOS)* | Edge 131+ (Desktop & Android; iOS requires iOS 26+) | 🟢 Ready | 🟡 In Progress *(Inherits Chromium MTC support)* | KEM: `X25519MLKEM768` (`0x11EC`) | Enabled by default in Edge 131+ via Chromium/BoringSSL for TLS 1.3 and HTTP/3 (QUIC), with enterprise group policy controls (`PostQuantumKeyAgreementEnabled`). ([Microsoft Edge Policies — PostQuantumKeyAgreementEnabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-policies#postquantumkeyagreementenabled)) |
| Mozilla Firefox | Gecko / NSS | Firefox 132+ (Desktop)<br>Firefox 145+ (Android) | 🟢 Ready | 🟡 In Progress | KEM: `X25519MLKEM768` (`mlkem768x25519`, `0x11EC`) | Enabled by default in TLS 1.3 and HTTP/3 (QUIC) on Desktop since Firefox 132 (Oct 2024) and on Android since Firefox 145 via NSS (`security.tls.enable_kyber` / `network.http.http3.enable_kyber`). ([Firefox 132.0 Release Notes](https://www.mozilla.org/en-US/firefox/132.0/releasenotes/), [Bugzilla #1919097](https://bugzilla.mozilla.org/show_bug.cgi?id=1919097)) |
| Opera | Blink / BoringSSL *(Desktop & Android)*; WebKit *(iOS)* | Opera 116+ (Chromium 131+; iOS requires iOS 26+) | 🟢 Ready | 🟡 In Progress *(Inherits Chromium MTC support)* | KEM: `X25519MLKEM768` (`0x11EC`) | Inherits Chromium 131+ BoringSSL default support for `X25519MLKEM768` in TLS 1.3 and HTTP/3 (QUIC). ([Chromium Platform Status #5085386357538816](https://chromestatus.com/feature/5085386357538816)) |

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
