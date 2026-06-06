# OpenEUDI

**Open-source TypeScript toolkit for verifying EU Digital Identity Wallet credentials.**

[![@openeudi/core](https://img.shields.io/npm/v/@openeudi/core?label=%40openeudi%2Fcore&color=2563eb)](https://www.npmjs.com/package/@openeudi/core)
[![@openeudi/openid4vp](https://img.shields.io/npm/v/@openeudi/openid4vp?label=%40openeudi%2Fopenid4vp&color=2563eb)](https://www.npmjs.com/package/@openeudi/openid4vp)
[![@openeudi/dcql](https://img.shields.io/npm/v/@openeudi/dcql?label=%40openeudi%2Fdcql&color=2563eb)](https://www.npmjs.com/package/@openeudi/dcql)
[![CI](https://github.com/openeudi/openid4vp/actions/workflows/ci.yml/badge.svg)](https://github.com/openeudi/openid4vp/actions/workflows/ci.yml)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](https://github.com/openeudi/core/blob/main/LICENSE)

The EU's [eIDAS 2.0 regulation (2024/1183)](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) requires all 27 member states to issue Digital Identity Wallets to citizens, and obliges large platforms and regulated sectors to *accept* them. The European Commission ships a reference *wallet* — but there is no open SDK for the **relying-party** side: the website or app that actually verifies a credential.

OpenEUDI fills that gap. It's the open-source, framework-agnostic, TypeScript-native reference implementation of the verifier side — so accepting an EU Wallet credential doesn't require a proprietary black box. All Apache-2.0, published to npm, developed in the open.

> **Status:** `@openeudi/core` & `@openeudi/openid4vp` v0.8.0 · `@openeudi/dcql` v0.2.0 · OpenID Foundation conformance-tested in CI · tracking OpenID4VP 1.0 and the EUDI Architecture Reference Framework.

## Packages

| Package | What it does |
|---------|--------------|
| **[@openeudi/core](https://github.com/openeudi/core)** | Framework-agnostic EUDI Wallet verification engine — session management, pluggable storage, OpenID4VP flow orchestration. |
| **[@openeudi/openid4vp](https://github.com/openeudi/openid4vp)** | Production-grade OpenID4VP verifier — SD-JWT VC + mDOC/mDL credentials, X.509 chain validation, OCSP/CRL revocation, EU Trusted List integration, encrypted responses. Tested against the OpenID Foundation conformance suite in CI. |
| **[@openeudi/dcql](https://github.com/openeudi/dcql)** | Zero-dependency DCQL (Digital Credentials Query Language) validator and credential matcher with detailed failure reasons. |

## Quick start

```bash
npm install @openeudi/core
```

```ts
import { VerificationService, DemoMode, VerificationType } from "@openeudi/core";

const service = new VerificationService({ mode: new DemoMode() });

// Strongly-typed events — event-name typos are caught at compile time
service.on("session:verified", (session, result) => {
  console.log("Verified:", result.country, "· age check:", result.ageVerified);
});

const session = await service.createSession({ type: VerificationType.BOTH });
console.log(session.walletUrl); // openid4vp://verify?session=<uuid> — render as a QR code
```

Swap `DemoMode` for `MockMode` in tests, or wire `@openeudi/openid4vp` for real wallet verification. See each package's README for the full API.

## Why open

Protocol-verification code — like TLS and HTTP libraries before it — should be open, auditable, and free. Digital identity is becoming public infrastructure across 450M EU citizens; the code that verifies it shouldn't be locked behind closed vendors.

## Support this work

OpenEUDI tracks a moving regulatory and cryptographic target — the OpenID4VP, SD-JWT, and ISO mDOC specs, plus EU Trusted List changes across member states. [**Sponsorship**](https://github.com/sponsors/openeudi) funds the maintenance that keeps it safe and usable: spec tracking, security patches, Trusted List sync, conformance testing, and documentation.

## Links

[npm org](https://www.npmjs.com/org/openeudi) · [@openeudi/core](https://www.npmjs.com/package/@openeudi/core) · [@openeudi/openid4vp](https://www.npmjs.com/package/@openeudi/openid4vp) · [@openeudi/dcql](https://www.npmjs.com/package/@openeudi/dcql) · [Sponsor](https://github.com/sponsors/openeudi)

Maintained by [Akos Foldesi](https://github.com/openeudi) · Apache-2.0
