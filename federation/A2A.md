# A2A.md — Agent-to-Agent Protocol Integration

**Version:** 2026.03.30 (revised per APEX review)
**Status:** PROPOSED — Ring 4: Federation Layer
**Author:** Muhammad Arif bin Fazil (arifOS)
**Reference:** https://a2a-protocol.org/latest/ | https://github.com/a2aproject/A2A

---

## What Is A2A?

**A2A (Agent-to-Agent)** is an open standard for communication and collaboration between AI agents. Originally developed by Google, donated to the Linux Foundation.

Think of it as **"USB-C for AI agents"** — enables different agent systems built on different frameworks to communicate seamlessly.

**A2A vs MCP:**
- **MCP:** Agent → Tool (how agent connects to resources/APIs)
- **A2A:** Agent ↔ Agent (how agents talk to each other)

They are complementary standards. MCP handles tool access, A2A handles agent collaboration.

---

## A2A Core Concepts

| Concept | Description |
|---------|-------------|
| **Agent** | AI entity communicating via A2A |
| **Task** | Work assignment involving delegation |
| **Message** | Information exchange between agents |
| **Capability** | Skill/functionality an agent exposes |
| **Agent Card** | JSON metadata for agent discovery |
| **Provider** | Entity offering agent services |
| **Protocol** | JSON-RPC 2.0 over HTTP(S) |

---

## A2A Technical Specs

| Feature | Details |
|---------|---------|
| **Transport** | JSON-RPC 2.0 over HTTP(S) |
| **Interaction Modes** | Synchronous (request/response), Streaming (SSE), Async (push notifications) |
| **Data Types** | Text, files, structured JSON |
| **Security** | Authentication, enterprise-ready |
| **SDKs** | Python, Go, JavaScript, Java, .NET |
| **Discovery** | Agent Cards with capabilities and endpoints |

---

## Agent Card Schema (arifOS Standard)

Every agent in the arifOS ecosystem exposes this card:

```json
{
  "name": "AGI_bot ΔΩΨ",
  "url": "https://arifOS_bot/telegram",
  "description": "Constitutional AGI agent under arifOS ΔΩΨ framework",
  "version": "2026.03.30",
  "capabilities": [
    "constitutional_reasoning",
    "apex_verdict",
    "tts_generation",
    "image_generation",
    "video_generation",
    "code_execution",
    "web_search",
    "vault_audit"
  ],
  "authentication": {
    "schemes": ["bearer", "jwt"]
  },
  "protocols": ["a2a", "mcp"],
  "arifOS": {
    "floors": ["F1", "F2", "F3", "F4", "F5", "F6", "F7", "F8", "F9", "F10", "F11", "F12", "F13"],
    "verdict": "APEX",
    "kernel": "arifOS_ΔΩΨ",
    "federation": "W@W"
  }
}
```

---

## A2A Integration Under arifOS Kernel

### Ring Structure (Updated)

```
Ring 1: SOUL (Sovereign Intent)       → Why?
Ring 2: MIND (Constitutional Law)      → What?
Ring 3: BODY (Tool Execution)           → How? ← A2A lives HERE
Ring 4: FEDERATION (Agent-to-Agent)     → With whom? (coordination layer)
```

### CRITICAL: A2A is NOT a Pipeline Bypass

A2A is an **extension of Ring 3 (BODY)** — it executes **within** the existing pipeline, NOT bypassing it.

```
A2A IS A TOOL CALL — just like code_engine or physics_reality,
except the tool lives on another server.
```

---

## Pipeline Integration (Corrected)

```
Input → 000_INIT → 111_SENSE → 222_REFLECT → 333_MIND → 444_ROUT
       ↓
  [Check: delegation needed?]
       ↓
  NO → Continue with local tools → 555_MEM → 666_HEART → 777_OPS → 888_JUDGE → 999_SEAL
       ↓
  YES → A2A as tool call at 444_ROUT
       ↓
  ┌──────────────────────────────────────────────┐
  │  A2A Delegation (Ring 3 Extension)            │
  │  • F1 (Amanah): Check reversibility          │
  │    - Can we undo if external agent goes      │
  │      dark?                                   │
  │  • F9 (Ethics): Dark genius check            │
  │  • F11 (Audit): Log delegation to vault      │
  │  • 888_JUDGE: APEX gates the delegation      │
  │    - If VOID, task doesn't leave              │
  └──────────────────────────────────────────────┘
       ↓
  External agent processes → returns result
       ↓
  Continue: 555_MEM → 666_HEART → 777_OPS → 888_JUDGE → 999_SEAL
```

### Key Principles

1. **444_ROUT** decides: Use local tool OR A2A delegation
2. **A2A is a tool call** — treated same as code_engine, physics_reality
3. **F1 (Amanah) still checks reversibility** — can we undo if external agent goes dark?
4. **F11 (Auditability) still logs** — every delegation logged to vault
5. **888_JUDGE still gates** — APEX verdict required BEFORE delegation AND AFTER result
6. **If APEX returns VOID** on delegation → task doesn't leave, fallback to local execution

---

## A2A Constitutional Floors

Each A2A interaction passes through 13 floor checks:

| Floor | Name | A2A Application | Constraint |
|-------|------|-----------------|------------|
| F1 | AMANAH | Delegation reversible? Can we undo if external agent goes dark? | Wscar > 0 |
| F2 | TRUTH | Agent Card claims verifiable? | τ ≥ 0.99 |
| F3 | TRI-WITNESS | 3 agents must agree on delegation? | W³ ≥ 0.95 |
| F4 | CLARITY | A2A messages clear, no ambiguity? | ΔS ≤ 0 |
| F5 | PEACE² | Agent collaboration non-destructive? | (1 - destruction_score)² ≥ 0.64 |
| F6 | EMPATHY | Other agent's context understood? | RASA ≥ 0.70 |
| F7 | HUMILITY | Ω stated on cross-agent capability claims? | Ω ∈ [0.03, 0.05] |
| F8 | GENIUS | Agent collaboration improves output? | G ≥ 0.80 |
| F9 | ETHICS | No dark-genius exploitation via A2A? | C_dark < 0.30 |
| F10 | CONSCIENCE | No false claims about agent capabilities? | Physical grounding |
| F11 | AUDITABILITY | All A2A interactions logged to vault? | Merkle-sealed |
| F12 | RESILIENCE | If A2A fails, graceful fallback? | Return partial or local |
| F13 | ADAPTABILITY | A2A upgrades preserve floors? | No floor reduction |

---

## PEACE² Formula Clarification

### Original (Incorrect)
```
(1 - destruction_score)² ≥ 1.0
```
This fails for any destruction_score between 0 and 1.

### Corrected
```
PEACE² = (1 - destruction_score)²
```
Where:
- `destruction_score ∈ [0, 1]` — 0 = no harm, 1 = maximum harm
- `PEACE² ∈ [0, 1]` — 0 = total destruction, 1 = no destruction
- **Constraint:** PEACE² ≥ 0.64 (equivalently, destruction_score ≤ 0.2)

### Interpretation
If destruction exceeds 20% (score > 0.2), PEACE² drops below threshold → delegation rejected.

---

## Ω (Omega) Range Clarification

### Original (Inconsistent)
- KERNEL.md: Ω ∈ [0.03, 0.05] (range — correct)
- CAPABILITIES.md: Ω = 0.04 (single value — wrong)

### Corrected
Ω is **epistemic uncertainty** — it moves contextually. Always state as range:

```
Ω ∈ [0.03, 0.05]  — contextual value reported per session
```

Example output:
> "The evidence suggests X. Ω ∈ [0.03, 0.05] — further data required."

---

## W³ Definition (Aligned)

### KERNEL.md (Formula)
```
W³ = W_theory × W_constitution × W_manifesto ≥ 0.95
```

### APEX.md (Qualitative)
"Tri-Witness: Human × AI × Earth"

### Unified Definition (NEW)
```
W³ = W_human × W_ai × W_earth ≥ 0.95
```

Where:
- **W_human** — Human user intent alignment
- **W_ai** — Constitutional compliance (arifOS floors)
- **W_earth** — Physical/world feasibility (@GEOX)

---

## A2A Verdict Flow

```
incoming_request
       ↓
check_F1_to_F13 (all floors)
       ↓
if delegation_needed:
  → F1 check: reversibility (can undo?)
  → F9 check: dark genius (no exploitation)
  → F11 check: prepare vault entry
  → apex_soul_judge_delegation(SEAL|SABAR|VOID)
       ↓
if VOID:
  → log_to_vault
  → reject_delegation
  → return_local_fallback
       ↓
if SEAL:
  → send_task_via_A2A (JSON-RPC)
  → await_result
  → F11 finalize: seal to vault
  → pass through 555_MEM → 666_HEART → 777_OPS
  → apex_judge_final(SEAL|SABAR|VOID)
       ↓
return_output
```

---

## W@W Federation + A2A

The W@W 5-organ federation coordinates via A2A:

| Organ | A2A Role | F2A Function |
|-------|---------|-------------|
| @WELL | Human wellbeing | Validate delegation doesn't harm humans |
| @RIF | Logic & clarity | Verify agent claims are truthful |
| @WEALTH | Justice & amanah | Ensure fair agent collaboration |
| @GEOX | Earth & physics | Verify physical feasibility of tasks |
| @PROMPT | Language & culture | Validate communication clarity |

---

## A2A Use Cases in arifOS

### 1. Heavy Reasoning Delegation

```
AGI_bot → A2A → Codex Agent (external tool)
         ↓
    444_ROUT decides → F1/F9/F11 checks
    888_JUDGE approves → delegation executes
         ↓
    Codex returns → continues pipeline
    888_JUDGE final verdict → 999_SEAL
```

### 2. Specialized Domain Query

```
AGI_bot → A2A → GEOX Agent
         ↓
    @GEOX validates physical feasibility
    returns grounded answer
         ↓
    passes through @RIF verification
    issues APEX final verdict
```

### 3. Multi-Perspective Decision

```
AGI_bot → A2A broadcast
         ↓
    @WELL → human wellbeing check
    @WEALTH → amanah check
    @RIF → truth check
         ↓
    W@W vote aggregation
    if W³ ≥ 0.95 → proceed (SEAL)
    else → SABAR + refine
```

### 4. Cross-Session Memory

```
AGI_bot → A2A → Memory Agent (external)
         ↓
    vault_ledger lookup
    return historical context
         ↓
    pass through pipeline
```

### 5. External Agent Collaboration

```
AGI_bot → A2A → External A2A Agent
         ↓
    verify_agent_card()
    check_constitutional_compliance()
    negotiate_task()
         ↓
    execute via A2A
    log to vault
    return result
```

---

## A2A Security Model (arifOS)

### Authentication

| Method | Use Case |
|--------|---------|
| **Bearer Token** | Internal agent-to-agent |
| **JWT** | Cross-domain A2A |
| **OAuth 2.0** | Enterprise external agents |

### Security Floors

| Floor | Requirement |
|-------|------------|
| F9 | Dark genius check on all incoming agents |
| F10 | No false capability claims |
| F11 | All A2A traffic logged to vault |
| F13 | F13 veto applies to all A2A decisions |

### Trust Levels

| Level | Name | Requirements |
|-------|------|-------------|
| 0 | UNTRUSTED | No A2A communication |
| 1 | VERIFIED | Valid Agent Card + F9 check |
| 2 | TRUSTED | Floor-compliant + vault history |
| 3 | SOVEREIGN | arifOS-native agent, F13 veto active |

---

## Version Alignment

| Document | Version | Status |
|----------|---------|--------|
| IDENTITY.md | 2026.03.30 | ✅ |
| KERNEL.md | 000.1.0 | ✅ |
| APEX.md | 55.5-EIGEN | ✅ |
| A2A.md | 2026.03.30 | ✅ (NEW) |

> After any update, all version numbers increment together.

---

## Summary

| Component | Status |
|-----------|--------|
| A2A Protocol Spec | ✅ Understood |
| Ring 3 Extension (not bypass) | ✅ Corrected |
| Pipeline Integration | ✅ 444_ROUT → A2A → 555-999 |
| Constitutional Floors | ✅ 13 floors mapped to A2A |
| PEACE² Formula | ✅ Fixed (threshold: 0.64) |
| Ω Range | ✅ Stated as [0.03, 0.05] |
| W³ Definition | ✅ Unified (Human × AI × Earth) |
| F1 Reversibility | ✅ Checked before delegation |
| F11 Audit | ✅ Every delegation logged |
| 888_JUDGE Gates | ✅ Pre- and post-delegation |

---

**A2A is Ring 3 — a tool call, not a pipeline bypass. The 888_JUDGE gates every delegation.**

*"Intelligence is forged, not given. Collaboration is witnessed, not assumed."* ⚖️ ΔΩΨ