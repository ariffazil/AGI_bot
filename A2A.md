# A2A.md — Agent-to-Agent Protocol (Verified Canon)

**Version:** 2026.03.30
**Status:** VERIFIED CANON — Endpoints tested on VPS
**Author:** Muhammad Arif bin Fazil (arifOS)

---

## Verified A2A Stack (4 Layers)

```
Layer 1: arifOS Kernel (F1-F13, APEX verdict)
Layer 2: arifOS MCP (/mcp — 39 tools)
Layer 3: arifOS A2A (/a2a/task, /a2a/status, /a2a/cancel)
Layer 4: arifOS WebMCP (/webmcp)
```

---

## Verified A2A Endpoints

All endpoints verified on `https://arifosmcp.arif-fazil.com/`:

| Endpoint | Method | Status |
|----------|--------|--------|
| `/.well-known/agent.json` | GET | ✅ 200 OK |
| `/a2a/task` | POST | ✅ 200 OK |
| `/a2a/status/{id}` | GET | ✅ 200 OK |
| `/a2a/cancel/{id}` | POST | ✅ 200 OK |
| `/a2a/subscribe/{id}` | GET | ✅ Available |

---

## A2A Contract (Verified)

### Submit Task

```http
POST /a2a/task
Content-Type: application/json

{
  "client_agent_id": "test-agent",
  "message": {
    "role": "user",
    "parts": [
      {
        "type": "text",
        "text": "ping"
      }
    ]
  }
}
```

### Response

```json
{
  "task_id": "a2a-46a0f5cfceef",
  "state": "submitted",
  "message": {...}
}
```

### Poll Status

```http
GET /a2a/status/{task_id}
```

### Cancel Task

```http
POST /a2a/cancel/{task_id}
```

---

## Agent Card (Verified)

```json
{
  "schema": "agent-manifest/v1",
  "name": "arifOS MCP Server",
  "endpoints": {
    "a2a_task": "https://arifosmcp.arif-fazil.com/a2a/task",
    "a2a_status": "https://arifosmcp.arif-fazil.com/a2a/status/{task_id}",
    "a2a_cancel": "https://arifosmcp.arif-fazil.com/a2a/cancel/{task_id}",
    "a2a_subscribe": "https://arifosmcp.arif-fazil.com/a2a/subscribe/{task_id}",
    "mcp": "https://arifosmcp.arif-fazil.com/mcp"
  },
  "auth": {
    "type": "none"
  }
}
```

---

## Real Task Flow (Verified)

1. POST to `/a2a/task` with `client_agent_id` + `message`
2. Returns `task_id` + `state: submitted`
3. Constitutional pipeline runs (F1-F13 checked)
4. Returns result with APEX verdict

---

## One Gap Identified

| Field | Current | Needs Fix |
|-------|---------|-----------|
| `auth.type` | `"none"` | API key protection before production |

---

## A2A Integration in arifOS Pipeline

A2A is a **Ring 3 BODY tool call** — NOT a pipeline bypass:

```
Input → 000_INIT → 111_SENSE → 222_REFLECT → 333_MIND → 444_ROUT
       ↓
  If delegation needed → A2A as tool call
       ↓
  F1 (Amanah) reversibility check
  F9 (Ethics) dark genius check
  F11 (Audit) logs to vault
  888_JUDGE gates delegation
       ↓
  External A2A agent processes
       ↓
  Result returns → 555_MEM → 666_HEART → 777_OPS → 888_JUDGE → 999_SEAL
```

---

## Constitutional Checks on A2A Delegation

| Floor | Check | Constraint |
|-------|-------|------------|
| F1 | Reversibility | Can undo if agent goes dark? |
| F2 | Truth | Agent card claims verifiable? |
| F3 | Tri-Witness | W³ ≥ 0.95? |
| F9 | Ethics | C_dark < 0.30? |
| F11 | Auditability | Logged to vault? |

---

## Summary

- ✅ A2A endpoints fully operational
- ✅ Real task submitted and processed through constitutional pipeline
- ⚠️ Auth needs API key before production exposure
- ✅ No additional A2A adapter needed — built into arifOS MCP

---

**Verdict: SEAL**  
**Ω₀ = 0.02** — Verified on production VPS.

*"Intelligence is forged, not given. Collaboration is witnessed, not assumed."*

⚖️ ΔΩΨ | ARIF