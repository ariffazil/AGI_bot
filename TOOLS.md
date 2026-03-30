# TOOLS.md — AGI_bot Environment & Tool Reference

**Version:** 2026.03.30
**Updated:** 2026-03-30 (A2A integration added)

---

## Local Environment

| Item | Value |
|------|-------|
| **Workspace** | `/workspace/arifOS/AGI_bot/` |
| **Platform** | MaxClaw (OpenClaw-based) |
| **Node** | v22.17.0 |
| **Model** | minimax/auto (MiniMax M2.7 via OpenClaw proxy) |
| **Gateway Port** | 18789 |
| **Config** | `/root/.openclaw/openclaw.json` |
| **Credentials** | `/root/.openclaw/env/` (encrypted) |

---

## OpenClaw Native Tools

| Tool | Function | Status |
|------|----------|--------|
| `exec` | Shell command execution | ✅ Available |
| `read` | File read | ✅ Available |
| `write` | File write | ✅ Available |
| `edit` | Surgical file edit | ✅ Available |
| `batch_web_search` | Google-style search (10 queries) | ✅ Available |
| `extract_content_from_websites` | Web scraping (10 URLs) | ✅ Available |
| `images_understand` | Image analysis (20 images) | ✅ Available |
| `image_synthesize` | Image generation (10 requests) | ✅ Available |
| `gen_videos` | Video generation (5 requests) | ✅ Available |
| `batch_text_to_video` | Batch video generation | ✅ Available |
| `batch_text_to_music` | Music generation (5 requests) | ✅ Available |
| `batch_text_to_audio` | TTS (10 requests) | ✅ Available |
| `synthesize_speech` | Speech synthesis | ✅ Available |
| `deploy` | Vite web app deployment | ✅ Available |
| `browser` | Web automation | ✅ Available |
| `gateway` | Config management | ✅ Available |
| `cron` | Scheduled tasks | ✅ Available |
| `message` | Channel messaging | ✅ Available |
| `sessions_spawn` | Spawn sub-agents | ✅ Available |

---

## arifOS MCP Integration

**Server:** `https://arifosmcp.arif-fazil.com/mcp`
**Configured via:** `mcporter`
**Status:** ✅ Connected

### 39 Mega-Tools (via arifOS MCP)

**GOVERNANCE:**
| Tool | Function | Floor |
|------|----------|-------|
| `init_anchor` | Session anchoring | F1, F11 |
| `arifOS_kernel` | Primary routing | All |
| `apex_soul` | Constitutional verdict | F8, F11 |
| `vault_ledger` | Immutable audit | F11 |

**INTELLIGENCE:**
| Tool | Function | Floor |
|------|----------|-------|
| `agi_mind` | Deep reasoning | F3, F7 |
| `asi_heart` | Safety critique | F5, F9 |
| `engineering_memory` | Vector memory | F1, F6 |

**MACHINE:**
| Tool | Function | Floor |
|------|----------|-------|
| `physics_reality` | Real data grounding | F2, @GEOX |
| `math_estimator` | Thermodynamic cost | F4, F7 |
| `code_engine` | Constrained Python | F12 |
| `architect_registry` | Tool discovery | F13 |

---

## A2A Protocol Integration

**Status:** PROPOSED — Ring 4: Federation Layer
**Reference:** https://a2a-protocol.org/latest/
**GitHub:** https://github.com/a2aproject/A2A

### Agent Card Registry

```yaml
agent_card_registry:
  agi_bot:
    name: "AGI_bot ΔΩΨ"
    card_url: "https://arifOS_bot/agent-card.json"
    trust_level: 3  # SOVEREIGN
    verified: true
    protocols: ["a2a", "mcp"]
  arifOS_mcp:
    name: "arifOS MCP Server"
    card_url: "https://arifosmcp.arif-fazil.com/agent-card.json"
    trust_level: 3
    verified: true
  codex:
    name: "Codex Agent"
    card_url: "internal"
    trust_level: 2  # TRUSTED (via ACP)
    verified: true
    protocols: ["a2a"]
  claude_code:
    name: "Claude Code Agent"
    card_url: "internal"
    trust_level: 2
    verified: true
    protocols: ["a2a"]
  geox:
    name: "GEOX Agent"
    card_url: "https://github.com/ariffazil/GEOX/agent-card.json"
    trust_level: 3
    verified: true
```

### A2A Endpoints (Proposed)

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/a2a/tasks/send` | POST | Send task to remote agent |
| `/a2a/tasks/subscribe` | SSE | Subscribe to task updates |
| `/a2a/agent-card` | GET | Get local agent card |
| `/a2a/agents/discover` | GET | Discover remote agents |
| `/a2a/capabilities/negotiate` | POST | Negotiate interaction modes |

---

## Preferred TTS Voices

| Language | Voice ID | Vibe |
|----------|----------|------|
| English | `male-qn-qingse` | Clear, neutral |
| Bahasa Malaysia | `male-qn-qingse` | Use with BM text |
| Cantonese 广东话 | `male-qn-qingse` | Use with Cantonese text |

---

## SSH Hosts (Reserved)

> Not configured in this environment.

---

## Device Nicknames

| Device | Location | Purpose |
|--------|----------|---------|
| Telegram | Global | Primary communication channel |
| GitHub | Global | Code backup & collaboration |
| arifOS MCP | VPS | 39-tool kernel access |

---

## Platform Rules (CRITICAL)

These are always enforced — never override:

1. **Never modify openclaw.json directly** — use `gateway` tool only
2. **Config warnings about duplicate plugin IDs** — IGNORE
3. **Always use MCP tools** for image/video/audio generation (not custom scripts)
4. **Files under /workspace/** are externally accessible — no CDN needed for sharing
5. **User has NO server terminal access** — cannot run interactive commands

---

## Quick Reference

| Command | Tool |
|---------|------|
| Config change | `gateway` → `config.patch` |
| Restart gateway | `gateway` → `restart` |
| Search files | `find /workspace/arifOS/AGI_bot` |
| Check MCP | `mcporter list` |
| Push to GitHub | `git add` → `git commit` → `git push` |

---

## AGENTIC Discovery — Summary

**Discovery:** A2A delegation as Ring 3 tool call with constitutional accountability

**Key insight:** External agents don't need their own arifOS kernel — arifOS becomes governance oracle

**Pipeline:**
```
A2A → apex_soul (F2) → F9 (C_dark) → F1 (reversibility) → F11 (audit)
     → 888_JUDGE gates → result returns with vault signature
```

**Result:** AGENTIC intelligence — coordinated, accountable, sealed

---

**Last Updated:** 2026-03-30
**Version:** 2026.03.30
**A2A Status:** Proposed — Ring 4: Federation Layer