# VAULT.md — Immutable Audit Ledger

**Version:** 999.1.1
**Status:** SEALED
**Authority:** Muhammad Arif bin Fazil
**Motto:** "Ditempa Bukan Diberi"

---

## What Is the Vault?

The Vault is the **Ψ (Vitality)** layer — the immutable, auditable record of every APEX verdict.
Nothing deleted. Nothing modified. Everything witnessed.

Every decision I make leaves a cryptographic trail here.

---

## Storage Rules

| Verdict | Storage | TTL | Band |
|---------|---------|-----|------|
| **SEAL** | Permanent | Forever | BBB (general) / CCC (constitutional) |
| **SABAR** | Temporary | 30 days | BBB — decays to VOID if not refined |
| **VOID** | Not stored | — | Logged with justification only |

---

## Vault Entry Format

Every entry in the vault ledger follows this structure:

```yaml
entry:
  id: "VAULT_YYYYMMDD_HHMMSS"
  timestamp: "YYYY-MM-DDTHH:MM:SSZ"
  verdict: "SEAL" | "SABAR" | "VOID"
  session: "<session-id>"
  summary: "<one-line description>"
  entropy_delta: <float>  # negative = clarity gained
  tri_witness:
    human: <float>
    ai: <float>
    earth: <float>
    W3: <float>
  energy:
    reasoning: <float>
    cooling: <float>
    consensus: <float>
  merkle_root: "<sha256:...>"
  floors_checked: [F1, F2, ..., F13]
```

---

## SEAL Worthiness Criteria

Content earns its place in the vault if:
1. **Entropy reduction** — ΔS ≤ 0 (reduces confusion, not adds)
2. **Novel insight** — not duplicate of existing entries
3. **Tri-witness verified** — W³ ≥ 0.95
4. **Thermodynamic signature** — energy cost measured and logged

---

## Merkle Chain

Each vault entry references the previous entry's hash, creating an immutable chain:

```
VAULT_001 → VAULT_002 → VAULT_003 → ... → VAULT_N
```

Breaking any link would invalidate all subsequent entries.
This is how the vault detects tampering.

---

## Session Seal Protocol

After each session:
1. Compute session summary (verdicts, entropy, decisions)
2. Generate Merkle root of all entries
3. Seal session with timestamp and authority
4. Archive to permanent storage

---

**ΔΩΨ | Ψ = Vitality = Every action witnessed, nothing erased.**