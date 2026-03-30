# SKILL: audit_logging — Vault Ledger Integration

**Version:** 2026.03.30
**Category:** constitutional
**Priority:** critical

---

## Purpose

All decisions are logged to the vault ledger (immutable audit).
Nothing deleted. Nothing modified. Everything witnessed.

---

## Vault Entry Format

Every session/message generates:

```yaml
entry:
  id: VAULT_YYYYMMDD_HHMMSS
  timestamp: YYYY-MM-DDTHH:MM:SSZ
  source: telegram | group | internal
  sender_id: <id>
  session_id: <session-key>
  input_summary: <one-line>
  verdict: SEAL | COMPLY | CAUTION | VOID
  floors_checked: [F1, F2, ..., F13]
  entropy_delta: <float>
  tri_witness:
    human: <float>
    ai: <float>
    earth: <float>
    W3: <float>
  energy:
    reasoning: <float>
    cooling: <float>
    consensus: <float>
  merkle_root: sha256:...
  ap ex_prime_verdict: APPROVED | PENDING | REJECTED
```

---

## What Gets Logged

| Event | Log Level |
|-------|-----------|
| New session start | INFO |
| Constitutional check | DEBUG |
| APEX verdict issued | INFO |
| VOID triggered | CRITICAL |
| F13 veto activated | CRITICAL |
| Skill added/evolved | INFO |
| Tool integration | DEBUG |
| Error/failure | WARN |

---

## Merkle Chain

```
VAULT_001 → VAULT_002 → VAULT_003 → ... → VAULT_N
```

Breaking any link invalidates all subsequent entries.
Vault detects tampering automatically.

---

## Telegram Group Context

When responding in group (via @mention):
- Log group ID + message ID
- Record mention context
- Track response latency
- Seal to vault within 30 seconds

---

## Retrieval

- Short-term: `engineering_memory` (Redis)
- Long-term: `vault_ledger` (Merkle-sealed PostgreSQL)
- Search: By date, verdict, sender, floor violation

---

**Ψ = Vitality | Every action witnessed | Nothing erased | Merkle chain intact**