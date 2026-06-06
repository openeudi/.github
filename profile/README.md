# OpenEUDI

**Open-source TypeScript toolkit for verifying EU Digital Identity Wallet credentials.**

The EU's [eIDAS 2.0 regulation (2024/1183)](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) requires all 27 member states to issue Digital Identity Wallets to citizens, and obliges large platforms and regulated sectors to *accept* them. The European Commission ships a reference *wallet* — but there is no open SDK for the **relying-party** side: the website or app that actually verifies a credential.

OpenEUDI fills that gap. It's the open-source, framework-agnostic, TypeScript-native reference implementation of the verifier side — so accepting an EU Wallet credential doesn't require a proprietary black box. All Apache-2.0, published to npm, developed in the open.

## Packages

| Package | What it does |
|---------|--------------|
| **[@openeudi/core](https://github.com/openeudi/core)** | Framework-agnostic EUDI Wallet verification engine — session management, pluggable storage, OpenID4VP flow orchestration. |
| **[@openeudi/openid4vp](https://github.com/openeudi/openid4vp)** | Production-grade OpenID4VP verifier — SD-JWT VC + mDOC/mDL credentials, X.509 chain validation, OCSP/CRL revocation, EU Trusted List integration, encrypted responses. Tested against the OpenID Foundation conformance suite in CI. |
| **[@openeudi/dcql](https://github.com/openeudi/dcql)** | Zero-dependency DCQL (Digital Credentials Query Language) validator and credential matcher with detailed failure reasons. |

```bash
npm install @openeudi/core @openeudi/openid4vp @openeudi/dcql
```

## Why open

Protocol-verification code — like TLS and HTTP libraries before it — should be open, auditable, and free. Digital identity is becoming public infrastructure across 450M EU citizens; the code that verifies it shouldn't be locked behind closed vendors.

## Support this work

OpenEUDI tracks a moving regulatory and cryptographic target — the OpenID4VP, SD-JWT, and ISO mDOC specs, plus EU Trusted List changes across member states. [**Sponsorship**](https://github.com/sponsors/openeudi) funds the maintenance that keeps it safe and usable: spec tracking, security patches, Trusted List sync, conformance testing, and documentation.

Maintained by [Akos Foldesi](https://github.com/openeudi) · Apache-2.0
