# Security Policy — CryptoValidity

CryptoValidity is a security-first wallet designed for AI-assisted and
autonomous transaction execution. Security, privacy, and execution
integrity are core design goals, not optional features.

This document describes how security issues should be reported and how
CryptoValidity approaches vulnerability handling.

---

## Reporting a Security Vulnerability

If you believe you have discovered a security vulnerability in
CryptoValidity, please report it responsibly.

**Do NOT** open a public GitHub issue for security-sensitive findings.

### Preferred Contact
- Email: security@cryptovalidity.com  
  (or use a private channel provided by the maintainers)

Please include:
- a clear description of the issue
- steps to reproduce (if applicable)
- potential impact
- any proof-of-concept details (redacted where appropriate)

---

## Coordinated Disclosure

We follow a coordinated disclosure process:

1. Report received and acknowledged
2. Issue validated and scoped
3. Fix developed and reviewed
4. Disclosure coordinated when appropriate

We aim to acknowledge reports within **72 hours**.

---

## Security Design Principles

CryptoValidity is built around the following principles:

### 1. Deny-by-Default Execution
Transactions must not execute unless explicitly verified and authorized.

### 2. Separation of Intent and Execution
Transaction intent, authorization, and execution are treated as distinct
steps to reduce blast radius.

### 3. Minimal Trust Assumptions
AI agents, automation, and external systems are assumed to be fallible
or compromised.

### 4. Privacy as a Security Property
Balance visibility, transaction metadata, and execution context are
protected by default.

### 5. Defense-in-Depth
CryptoValidity is designed to integrate with execution-time
authorization systems (e.g., A2SPA) rather than relying on a single
control layer.

---

## Out of Scope

The following are considered out of scope for this repository:
- vulnerabilities in underlying blockchains
- third-party wallet integrations
- user key mismanagement outside CryptoValidity
- social engineering attacks unrelated to execution flow

---

## Status

This repository currently documents **architecture and security design**.
It is not yet a production wallet implementation.

Security posture will evolve as implementation work progresses.

---

## Final Note

Security is not a feature of CryptoValidity.
It is the reason CryptoValidity exists.
