# SECURITY_PLAYBOOK.md
**CryptoValidity — Secure AI Wallet**

## Purpose

This document defines how to reason about security in the CryptoValidity wallet.

CryptoValidity exists to address a growing failure mode in modern crypto systems:  
**transactions executed by software or AI without cryptographic proof of intent at execution time**.

Traditional wallets secure keys and identities, but they do not adequately secure **how, why, or under what constraints a transaction is executed**, especially when AI assistance or automation is involved.

CryptoValidity is designed to ensure that **every transaction execution is explicitly authorized, constrained, and verifiable**.

This playbook explains:
- The threat model CryptoValidity is built to address
- Security boundaries and assumptions
- Execution-time decision gates
- What must always be verified
- What must never happen

This document is intentionally **public-safe**. It contains no secrets, private keys, internal endpoints, or sensitive implementation details.

---

## Core Security Principle

> **Keys prove ownership.  
Authorization proves intent.  
Execution is the attack surface.**

CryptoValidity treats transaction execution—not key storage—as the highest-risk moment.

---

## What CryptoValidity Is (Security View)

CryptoValidity is a **secure crypto wallet architecture** designed for:
- AI-assisted transaction analysis
- Human-in-the-loop or autonomous execution
- Explicit authorization before funds move
- Verifiable execution and auditability

CryptoValidity separates:
- **Intent** (what the user or agent wants)
- **Authorization** (what is allowed)
- **Execution** (what actually happens on-chain)

This separation is critical when AI systems participate in transaction workflows.

---

## Threat Model

CryptoValidity assumes the following threats are **active and realistic**:

### 1. Unauthorized Transaction Execution
Transactions executed without explicit user or policy approval.

### 2. AI Overreach
AI assistants proposing or executing actions beyond their intended scope.

### 3. Payload or Parameter Mutation
Transaction parameters (amount, recipient, chain) altered after approval.

### 4. Replay Attacks
Previously authorized transactions re-submitted or re-used.

### 5. UI Trust Exploits
Users approving one action while a different action executes.

### 6. Delayed or Out-of-Context Execution
Transactions executed later, under different market or security conditions.

### 7. Key-Centric Security Fallacy
Assuming that key custody alone guarantees safe execution.

---

## Explicit Non-Goals

CryptoValidity does **not** attempt to:
- Guarantee profitable trades or decisions
- Prevent user error or poor judgment
- Replace blockchain consensus security
- Secure external protocols or smart contracts
- Eliminate all phishing or social engineering

CryptoValidity secures **execution**, not outcomes.

---

## Security Boundaries

### Inside the CryptoValidity Security Boundary
- Transaction intent capture
- Authorization constraints
- Execution-time verification
- Permission enforcement
- Replay protection
- Deterministic logging of execution outcomes

### Outside the CryptoValidity Security Boundary
- Blockchain network behavior
- External protocol correctness
- Market conditions
- Third-party contract security

If funds move, CryptoValidity assumes execution **must have been authorized first**.

---

## Required Execution Decision Gates

Before **any transaction executes**, all of the following must be true:

1. **Intent Integrity**
   - Transaction parameters match what was authorized
   - No silent modification is allowed

2. **Authorization Validity**
   - Approval is explicit (user, policy, or agent)
   - Authorization scope is enforced

3. **Permission Scope**
   - Asset, chain, amount, and direction are permitted
   - AI agents are constrained to their allowed actions

4. **Temporal Validity**
   - Authorization is fresh and within its allowed time window
   - Expired approvals are rejected

5. **Replay Protection**
   - Transactions cannot be reused or duplicated
   - Replays must fail deterministically

6. **Execution Context**
   - Execution matches the approved context
   - Cross-context execution is forbidden

If **any gate fails**, the transaction **must not execute**.

---

## Failure Handling Rules

- Failed authorization **blocks execution**
- Failures are logged and surfaced
- No silent fallback execution
- No “AI knows best” overrides
- No emergency bypasses without explicit user consent

Security failures are treated as **successful defenses**, not errors.

---

## Logging & Audit Expectations

Every execution attempt should produce an auditable record including:
- Transaction intent reference
- Authorization result
- Execution result (submitted / blocked)
- Timestamp
- Actor (user or agent)
- Reason for rejection (if applicable)

Audit logs are security guarantees, not analytics.

---

## Common Anti-Patterns (What Must Never Happen)

❌ Executing transactions solely because a key exists  
❌ Allowing AI to execute without scoped authorization  
❌ Modifying transaction details after approval  
❌ Replaying previously approved actions  
❌ Treating UI confirmation as sufficient proof  
❌ Allowing execution after authorization expiry  
❌ Prioritizing speed over authorization correctness  

Any of the above is a **security defect**.

---

## How to Reason About Changes

When reviewing changes, always ask:

1. Does this affect transaction execution?
2. Could this allow execution without explicit authorization?
3. Does this weaken AI or automation constraints?
4. Does this introduce ambiguity between intent and execution?
5. Would an attacker benefit from this change?

If uncertain, assume **risk** until proven otherwise.

---

## Security Review Triggers

A security review is required for changes that:
- Modify transaction flow
- Affect AI-assisted execution
- Alter approval or confirmation logic
- Touch replay protection or timing
- Introduce automation or autonomy
- Add bypasses or shortcuts

---

## Design Intent Summary

CryptoValidity exists because:
- Crypto transactions are irreversible
- AI increases speed and power
- Power without authorization is dangerous
- Execution must be provably intentional
- Authorization must precede execution

A wallet that cannot prove *why* a transaction executed cannot be considered secure.

---

## Final Rule

> **If funds move, intent must be provable.  
If intent is not provable, funds must not move.**

That rule is non-negotiable.
