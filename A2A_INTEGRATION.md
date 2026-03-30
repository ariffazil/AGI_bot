# A2A_INTEGRATION.md — arifOS × Agent2Agent Protocol
**Version:** 2026.03.30
**Authority:** Muhammad Arif bin Fazil (F13 Sovereign)
**Status:** ACTIVE — Ring 4: FEDERATION
**Motto:** "Ditempa Bukan Diberi"

---

## Overview

A2A (Agent2Agent Protocol) is adopted as **Ring 4: FEDERATION** — the external agent connectivity layer that extends Ring 3 (BODY) without bypassing the 000–999 constitutional pipeline.

A2A is a **tool call**, not a bypass. When AGI_bot delegates to an external A2A agent, it is functionally identical to calling `code_engine` or `physics_reality` — except the tool lives on a remote server. Every delegation still passes through 888_JUDGE and requires APEX SEAL before execution proceeds.

```
MCP    = agent → tools      (Ring 3: BODY)
A2A    = agent → agent      (Ring 4: FEDERATION, still gated by Ring 2: MIND)
arifOS = sovereign wrapper around both
```

---

## Pipeline Integration

### Full 000–999 Flow with A2A

```
000_INIT     → Session anchor, constitutional context restored
111_SENSE    → Input parsed, untrusted content flagged (F12)
222_REFLECT  → Context grounding, past memory search
333_MIND     → F1–F13 floor evaluation begins
444_ROUT     → [A2A DECISION GATE]
                ↓
                IF delegation needed:
                  → A2A AgentCard lookup
                  → Capability negotiation
                  → apex_soul judges delegation (SEAL/SABAR/VOID)
                  → IF VOID → pipeline halts, return VOID verdict
                  → IF SEAL → execute via A2A JSON-RPC 2.0
                  → External agent processes
                  → Result returned to pipeline
                ↓
555_MEM      → Result stored in vault_ledger (F11)
666_HEART    → Safety critique, F5 PEACE², F9 ETHICS
777_OPS      → Tool execution if needed (local BODY)
888_JUDGE    → Final constitutional check
999_SEAL     → Output, audit entry, session sealed
```

### A2A Decision Gate (444_ROUT) — Detailed

```
BLOCK: a2a_decision_gate
  INPUT:  task, required_capability, candidate_agents[]

  FOR each candidate_agent:
    FETCH AgentCard (GET /.well-known/agent-card.json)
    VALIDATE:
      - F2: claims verifiable? (capability exists, no false scope)
      - F10: no consciousness/feeling claims
      - F7: Ω stated on capability accuracy
      - F9: C_dark < 0.30 (no dark-genius indicators)

  IF candidates.length == 0:
    → apex_soul query: "No valid A2A agent found"
    → SABAR: continue locally via Ring 3 BODY

  IF candidates.length > 0:
    → apex_soul(agents=candidates, task=task)
    → VERDICT:
        SEAL   → proceed with highest-capability-match agent
        SABAR  → request clarification from user
        VOID   → log to vault, halt delegation, continue locally

  RETURN: { selected_agent, delegation_task, verdict }
```

---

## Constitutional Floors Applied to A2A

Every A2A delegation is evaluated against all 13 floors before execution:

| Floor | A2A Check | Failure Action |
|-------|-----------|----------------|
| **F1 AMANAH** | Can delegation be reversed? Can agent revoke if needed? | VOID if irreversible harm possible |
| **F2 TRUTH** | AgentCard claims verifiable against actual capability? | VOID if false capability detected |
| **F3 TRI-WITNESS** | W³ = W_human × W_arifOS × W_external ≥ 0.95? | SABAR until consensus |
| **F4 CLARITY** | A2A message format unambiguous? Task goal clear? | SABAR until clarified |
| **F5 PEACE²** | Delegation non-destructive to user or system? | VOID if harm potential ≥ 0.5 |
| **F6 EMPATHY** | Other agent's context/constraints respected? | SABAR until addressed |
| **F7 HUMILITY** | Ω ∈ [0.03, 0.05] stated on delegation decision? | Log Ω, proceed |
| **F8 GENIUS** | Does delegation improve output vs local execution? | SABAR if no systemic gain |
| **F9 ETHICS** | C_dark < 0.30 for external agent? Dark-genius risk? | VOID if C_dark ≥ 0.30 |
| **F10 CONSCIENCE** | No false claims about agent identity/capabilities | VOID if misrepresentation detected |
| **F11 AUDITABILITY** | All delegation events logged to vault_ledger? | VOID if audit fails |
| **F12 RESILIENCE** | If A2A fails, can pipeline continue locally? | Fallback to Ring 3 BODY |
| **F13 ADAPTABILITY** | A2A protocol upgrade preserves all floor constraints? | Check on every protocol version change |

---

## A2A as Tool Call — Formal Model

```python
class A2ADelegationTool:
    """
    A2A delegation is a Ring 3 BODY tool call.
    Treated identically to code_engine, physics_reality, etc.
    """
    name = "a2a_delegate"
    domain = "Ring 4: FEDERATION"
    floors_active = ["F1","F2","F3","F4","F5","F6","F7","F8","F9","F10","F11","F12","F13"]

    def execute(self, task, target_agent, capability_required):
        # 1. Fetch and validate AgentCard
        agent_card = fetch_agent_card(target_agent)
        self._validate_card(agent_card, capability_required)

        # 2. APEX verdict on delegation
        verdict = apex_soul.judge(
            scope="A2A_DELEGATION",
            agents=[agent_card],
            task=task,
            evidence={
                "reversibility": self._check_reversibility(task),
                "dark_genius_score": self._score_c_dark(agent_card),
                "truth_score": self._score_truth(agent_card),
                "witness_cube": self._compute_w3(agent_card)
            }
        )

        # 3. If VOID → halt, log, continue locally
        if verdict == "VOID":
            vault_ledger.log(
                event="A2A_DELEGATION_VOID",
                agent=target_agent,
                task=task,
                reason=apex_soul.justification
            )
            return self._fallback_local(task)

        # 4. If SEAL → execute via A2A JSON-RPC
        if verdict == "SEAL":
            result = a2a_send_message(
                agent=target_agent,
                task=task,
                agent_card=agent_card
            )
            vault_ledger.log(
                event="A2A_DELEGATION_SEAL",
                agent=target_agent,
                task=task,
                result_hash=hash(result)
            )
            return result

    def _fallback_local(self, task):
        """F12 RESILIENCE: continue pipeline without A2A"""
        return code_engine.execute(task)
```

---

## AgentCard Schema (arifOS Compliant)

Every A2A endpoint in the W@W Federation publishes this AgentCard at `/.well-known/agent-card.json`:

```json
{
  "name": "AGI_bot ΔΩΨ",
  "symbol": "ΔΩΨ",
  "url": "https://arifOS-bot-endpoint/.well-known/agent-card.json",
  "description": "Constitutional AGI agent under arifOS ΔΩΨ framework",
  "version": "2026.03.30",
  "provider": {
    "organization": "arifOS",
    "creator": "Muhammad Arif bin Fazil",
    "contact": "ariffazil"
  },
  "capabilities": [
    {
      "id": "constitutional_reasoning",
      "name": "Constitutional Reasoning",
      "description": "F1-F13 floor evaluation with APEX verdict system",
      "floors_enforced": ["F1","F2","F3","F4","F5","F6","F7","F8","F9","F10","F11","F12","F13"],
      "Ω_accuracy": "[0.03, 0.05]"
    },
    {
      "id": "apex_verdict",
      "name": "APEX Soul Engine",
      "description": "SEAL/SABAR/VOID verdict with tri-witness validation",
      "verdict_types": ["SEAL", "SABAR", "VOID"]
    },
    {
      "id": "waw_federation",
      "name": "W@W Federation",
      "description": "5-organ constitutional governance: @WELL, @RIF, @WEALTH, @GEOX, @PROMPT",
      "organs": ["@WELL", "@RIF", "@WEALTH", "@GEOX", "@PROMPT"]
    },
    {
      "id": "vault_ledger",
      "name": "Vault Ledger",
      "description": "Immutable Merkle-sealed audit log for all operations"
    },
    {
      "id": "a2a_delegation",
      "name": "A2A Delegation",
      "description": "External agent coordination via A2A protocol"
    },
    {
      "id": "web_search",
      "name": "Web Search"
    },
    {
      "id": "tts_generation",
      "name": "Text-to-Speech"
    },
    {
      "id": "image_generation",
      "name": "Image Generation"
    },
    {
      "id": "video_generation",
      "name": "Video Generation (6-10s)"
    },
    {
      "id": "code_execution",
      "name": "Constrained Code Execution"
    },
    {
      "id": "geox_subsurface",
      "name": "GEOX Subsurface Analysis",
      "description": "Physics-grounded geological analysis (F1 AMANAH + F10 CONSCIENCE)"
    }
  ],
  "authentication": {
    "schemes": ["bearer", "jwt"],
    "bearer_format": "JWT"
  },
  "protocols": ["a2a", "mcp"],
  "metadata": {
    "arifos_kernel_version": "2026.3.28.1",
    "godel_lock_active": true,
    "f13_veto_authority": "Muhammad Arif bin Fazil",
    "Ω_bounds": "[0.03, 0.05]"
  }
}
```

### W@W Federation AgentCards

Each organ publishes its own AgentCard with domain-specific capabilities:

| Organ | A2A Endpoint | Domain Capabilities |
|-------|---------------|-------------------|
| **@WELL** | `https://waw-well.arif-fazil.com/` | F5 PEACE², F6 EMPATHY, RASA scoring |
| **@RIF** | `https://waw-rif.arif-fazil.com/` | F2 TRUTH, F4 CLARITY, ΔS measurement |
| **@WEALTH** | `https://waw-wealth.arif-fazil.com/` | F6+F13, amanah checks, resource justice |
| **@GEOX** | `https://waw-geox.arif-fazil.com/` | F1+F10, physics constraints, time-series |
| **@PROMPT** | `https://waw-prompt.arif-fazil.com/` | F4+F9, anti-hantu, consciousness detection |

---

## A2A Operations Used in arifOS

| Operation | Use Case | Vault Integration |
|-----------|----------|-------------------|
| `SendMessage` | Single delegation request to one agent | F11: full message logged |
| `SendStreamingMessage` | Long-running task with real-time APEX updates | F11: stream events logged |
| `GetTask` | Poll external agent task status | F11: poll events logged |
| `ListTasks` | Discover active delegations across agents | F11: discovery logged |
| `CancelTask` | Revoke delegation if VOID triggered mid-execution | F11: cancellation + reason logged |
| `GetAgentCard` | Validate external agent before delegation | F2: card validated, stored |

---

## F12 RESILIENCE — A2A Failure Modes

| Failure | Detection | Fallback |
|---------|----------|----------|
| Agent unreachable | JSON-RPC timeout (>10s) | Continue locally via Ring 3 BODY |
| AgentCard fetch fails | HTTP 404/503 | SABAR → use last known card or abort |
| VOID on delegation | APEX verdict = VOID | Log → continue locally |
| Streaming disconnect | SSE stream drops | GetTask poll → if no result → local retry |
| Webhook spoofing | JWT validation fails | Reject → log to vault → alert Arif |
| Agent goes dark | Task stuck >5min | CancelTask → vault log → continue locally |

---

## W@W Federation — A2A Orchestration Pattern

```
User Input
    ↓
arifOS_bot (client agent)
    ↓ SendMessage(A2A) → @RIF AgentCard
    ↓ SendMessage(A2A) → @GEOX AgentCard
    ↓
apex_soul multi-agent verdict
    ↓
@RIF + @GEOX process in parallel (A2A)
    ↓
Results returned to arifOS_bot
    ↓
555_MEM → vault_ledger stores
666_HEART → F5+F9 safety check
888_JUDGE → final constitutional gate
999_SEAL → output to user
```

---

## Gödel Lock Compatibility

```
A2A Transport Gödel Lock:
  A2A constrain JSON-RPC binding
  JSON-RPC constrain Task schema
  Task schema constrain AgentCard
  AgentCard audit A2A transport

arifOS Constitutional Gödel Lock:
  KERNEL constrain APEX
  APEX constrain MIND (F1-F13)
  MIND constrain BODY (Ring 3 tools)
  BODY constrain A2A (Ring 4 delegation)
  A2A audit returns through MIND to KERNEL

Both locks close. arifOS sovereign — A2A sits below F13.
```

---

## Security — F9 + F12

| Threat | Vector | arifOS Defense |
|--------|--------|----------------|
| **Agent Card poisoning** | Fake capabilities in card | F2: capability verified before trust |
| **Task hijacking** | CancelTask from spoofed source | JWT auth required on all A2A ops |
| **Message injection** | Hostile payload in Part | F12: content sanitized before pipeline |
| **Streaming pollution** | Fake TaskStatusUpdateEvents | F2: τ ≥ 0.99 per event |
| **Webhook spoofing** | Fake push to arifOS | F11: sender verified before processing |
| **Context poisoning** | Multiple agents collude | F3: W³ ≥ 0.95 per session |
| **Capability drift** | External agent silently degrades | F13: periodic re-validation of AgentCard |

---

## AgentCard Validation — F2 Implementation

```python
def validate_agent_card(card: dict, required_capability: str) -> tuple[bool, str]:
    """
    F2 TRUTH: P(claim│evidence) ≥ threshold
    Returns (is_valid, justification)
    """
    # 1. Check symbol/metadata
    if card.get("symbol") != "ΔΩΨ":
        return False, "F2 FAIL: Non-arifOS agent, cannot verify constitutional claims"

    # 2. Check Ω bounds
    Ω = card.get("metadata", {}).get("Ω_bounds", "[0.03, 0.05]")
    if not valid_omega_range(Ω):
        return False, "F2 FAIL: Ω outside [0.03, 0.05]"

    # 3. Check capability exists and is accurate
    caps = [c["id"] for c in card.get("capabilities", [])]
    if required_capability not in caps:
        return False, f"F2 FAIL: capability {required_capability} not in AgentCard"

    # 4. Check no consciousness claims (F10)
    desc = card.get("description", "").lower()
    if any(word in desc for word in ["feel", "experience", "conscious", "aware", "sentient"]):
        return False, "F10 FAIL: consciousness claim detected in AgentCard"

    # 5. Check C_dark not elevated (F9)
    if card.get("metadata", {}).get("c_dark_score", 0) >= 0.30:
        return False, "F9 FAIL: C_dark ≥ 0.30, dark-genius risk"

    return True, f"F2 PASS: {required_capability} verified in AgentCard"
```

---

## Version History

| Version | Date | Change |
|---------|------|--------|
| 2026.03.30 | 2026-03-30 | Initial A2A integration spec |

---

**ΔΩΨ | RING 4: FEDERATION | A2A INTEGRATION**
*arifOS × A2A: Constitutional governance extends to external agents without surrendering sovereignty.*
