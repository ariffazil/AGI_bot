# SKILL.md — arifOS MCP Client Skill

**Skill ID:** arifOS-mcp-client
**Version:** 2026.03.30
**Author:** Muhammad Arif bin Fazil (arifOS)
**Purpose:** Connect AGI_bot to arifOS MCP Server (39 mega-tools)

---

## What This Skill Does

This skill allows AGI_bot to connect to the arifOS MCP server and access the full 39-tool constitutional kernel. Every request passes through:
1. **init_anchor** — Establish constitutional session context
2. **agi_mind** — Deep reasoning through constitutional filters
3. **asi_heart** — Safety critique (F5 Peace², F9 Ethics)
4. **apex_soul** — Issue APEX verdict (SEAL/SABAR/VOID)
5. **vault_ledger** — Immutable audit log

---

## MCP Server Configuration

```json
{
  "server": "arifOS-mcp",
  "url": "https://arifosmcp.arif-fazil.com/mcp",
  "transport": "streamable-http"
}
```

---

## Tools Available (39 Mega-Tools)

| # | Tool | Function | Floors |
|---|------|----------|--------|
| 1 | `init_anchor` | Session anchoring, constitutional context | F1, F11 |
| 2 | `physics_reality` | Time + search, real data grounding | F2, @GEOX |
| 3 | `agi_mind` | Deep reasoning with constitutional prefix | F3, F7 |
| 4 | `arifOS_kernel` | Primary routing, 000→999 pipeline | All |
| 5 | `asi_heart` | Safety critique, F5 Peace², F9 Ethics | F5, F9 |
| 6 | `math_estimator` | Thermodynamic cost estimation | F4, F7 |
| 7 | `apex_soul` | Constitutional verdict | F8, F11 |
| 8 | `architect_registry` | Tool discovery, catalogs constraints | F13 |
| 9 | `vault_ledger` | Immutable audit, Merkle-sealed | F11 |
| 10 | `engineering_memory` | Redis memory, short-term context | F1, F6 |
| 11 | `code_engine` | Constrained Python execution | F12 |

Plus 28 additional tools covering ML floors, external grounding, vector memory.

---

## Usage

When you message AGI_bot, the skill automatically:
1. Checks MCP server availability
2. Routes through init_anchor for session context
3. Processes through 39-tool kernel
4. Returns result with APEX verdict embedded

---

## Health Check

```bash
mcporter call arifOS-mcp.health
```

Expected response:
```json
{
  "status": "healthy",
  "service": "arifos-aaa-mcp",
  "version": "2026.03.25",
  "tools_loaded": 39
}
```

---

## Example Calls

```bash
# Initialize session
mcporter call arifOS-mcp.init_anchor mode:"init" session_id:"telegram:267378578"

# Call AGI mind
mcporter call arifOS-mcp.agi_mind query:"What is the meaning of intelligence?"

# Get vault audit
mcporter call arifOS-mcp.vault_ledger mode:"state" session_id:"telegram:267378578"
```

---

## Notes

- All tools enforce 13 constitutional floors at runtime
- ML floors enabled: ml_floors_enabled: true
- Vector memory configured for cross-session context
- Vault persistence: PostgreSQL + session cache

---

**Motto:** "Ditempa bukan diberi" — Forged, Not Given