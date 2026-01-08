# CryptoValidity FAQ
## Secure, Intent-Verified, Privacy-Aware Wallet Execution

---

## What is CryptoValidity?

CryptoValidity is a wallet architecture that enforces **execution-time authorization**
for digital asset transactions.

It ensures that **no transaction executes** unless the exact intent was explicitly
authorized, remains unmodified, is still valid, and complies with approved constraints
at the moment of execution.

CryptoValidity is designed for:
- automated and agent-driven transactions
- delegated execution
- delayed or scheduled payments
- environments where blind trust in signatures is insufficient

---

## Is CryptoValidity a wallet app?

CryptoValidity is a **wallet execution model and security architecture**, not a UI-first
consumer wallet application.

It can be implemented as:
- a smart wallet
- a custody control layer
- an agent-secured transaction gateway
- an execution guard for existing wallets

---

## How is CryptoValidity different from a normal crypto wallet?

Traditional wallets authorize transactions at **signing time**.

CryptoValidity authorizes transactions at **execution time**.

This means:
- signatures alone are not sufficient
- authorization must still be valid when the transaction executes
- constraints are enforced immediately before irreversible effects occur

---

## Does CryptoValidity replace private keys or signatures?

No.

CryptoValidity **does not replace** cryptographic signatures or key ownership.

It adds an **additional execution-time verification layer** that ensures:
- the signed transaction still matches approved intent
- the transaction is still permitted to execute
- automation cannot silently escalate privileges

---

## Is CryptoValidity a mixer or privacy coin?

No.

CryptoValidity is **not**:
- a mixer
- a tumbling service
- a privacy coin
- a transaction obfuscation protocol

CryptoValidity focuses on **execution control and privacy minimization**, not anonymity.

---

## Does CryptoValidity hide wallet balances?

CryptoValidity does not guarantee full balance anonymity.

It enforces **privacy by minimization**, meaning:
- systems SHOULD avoid exposing full balances unnecessarily
- execution logic SHOULD not require disclosure of unrelated holdings
- authorization and verification data SHOULD remain off-chain when possible

Advanced privacy techniques (e.g., zero-knowledge proofs) are **explicitly out of scope**
for the baseline specification.

---

## Can someone see how much money is in my wallet?

Blockchain visibility rules still apply.

CryptoValidity does not override:
- public ledger transparency
- chain-level explorers
- protocol-specific disclosure requirements

However, CryptoValidity **reduces balance exposure during execution flows** by ensuring
that:
- transactions are evaluated based on authorized intent
- systems do not require full balance visibility to approve execution

---

## How does CryptoValidity prevent unauthorized transactions?

CryptoValidity prevents unauthorized execution by enforcing:

- explicit transaction intent authorization
- cryptographic integrity checks
- freshness validation
- constraint enforcement at execution time

If verification fails, execution **MUST NOT** occur.

---

## What happens if an agent is compromised?

If an agent is compromised:
- it cannot execute transactions outside authorized intent
- it cannot escalate permissions beyond constraints
- it cannot replay expired or consumed authorizations

CryptoValidity assumes agents are **not inherently trusted**.

---

## Does CryptoValidity work with automated or scheduled payments?

Yes.

CryptoValidity is specifically designed for:
- delayed execution
- scheduled transfers
- agent-triggered payments
- delegated transaction execution

All automated execution remains subject to execution-time verification.

---

## Can CryptoValidity stop replay attacks?

Yes.

Replay protection is enforced at execution time using:
- freshness constraints
- nonces or sequence controls
- validity windows

Previously authorized intents cannot be reused outside their approved context.

---

## Is CryptoValidity compatible with smart contracts?

Yes.

CryptoValidity can be applied to:
- contract calls
- approvals and allowances
- programmable wallet logic
- agent-triggered contract execution

It does not require changes to blockchain consensus mechanisms.

---

## Does CryptoValidity require a specific blockchain?

No.

CryptoValidity is **chain-agnostic**.

It can be applied to:
- EVM-based chains
- account-based ledgers
- UTXO-like models (with adaptations)
- off-chain settlement systems

---

## How is CryptoValidity related to A2SPA?

A2SPA defines **execution-time authorization** as a general security control plane.

CryptoValidity applies A2SPA principles specifically to:
- wallet execution
- transaction settlement
- asset movement

A2SPA governs verification.
CryptoValidity governs wallet execution behavior.

---

## Is CryptoValidity open source?

This repository defines a **reference specification**.

Licensing and implementation details are defined separately and may vary depending on
deployment context.

---

## Is CryptoValidity compliant with regulations?

CryptoValidity does not bypass:
- regulatory requirements
- compliance obligations
- jurisdictional controls

It provides stronger execution guarantees that may **support compliance**, not evade it.

---

## What problems does CryptoValidity not solve?

CryptoValidity does **not**:
- guarantee anonymity
- hide all on-chain activity
- prevent poor user decisions
- secure model reasoning
- replace blockchain privacy layers
- eliminate the need for audits

It solves **execution-time trust**, not every security problem.

---

## Why does CryptoValidity matter now?

As wallets become:
- automated
- agent-driven
- embedded into applications
- capable of autonomous execution

**Signing alone is no longer sufficient.**

CryptoValidity exists to ensure that autonomy does not become blind trust.

---

## Where can I learn more?

See:
- `SPEC.md` — formal execution model
- `Threat_Model.md` — wallet-specific risks
- `SECURITY.md` — disclosure and scope
- A2SPA documentation for execution-time authorization principles
