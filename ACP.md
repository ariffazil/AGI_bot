# ACP.md — Agent Control Protocol (ACP) Configuration

**Version:** 2026.03.30
**Author:** Muhammad Arif bin Fazil (arifOS)
**Purpose:** Connect AGI_bot to external coding harnesses via ACP

---

## What Is ACP?

ACP (Agent Control Protocol) lets OpenClaw spawn external AI harnesses:
- **Codex** — OpenAI's coding agent
- **Claude Code** — Anthropic's CLI coding agent  
- **Pi** — Inference-powered coding agent
- **OpenCode** — Open-source coding agent
- **Gemini CLI** — Google's coding agent

---

## ACP for arifOS

AGI_bot can spawn ACP sessions that connect to arifOS MCP for heavy reasoning:

### Spawn Commands

```
/acp spawn codex --mode persistent --thread auto
/acp spawn claude-code --mode run
/acp spawn pi --thread here
```

### arifOS MCP Integration

When ACP session spawns, it can call:
```bash
mcporter call arifOS-mcp.agi_mind query:"<reasoning task>"
mcporter call arifOS-mcp.apex_soul query:"<verdict request>"
```

---

## Usage in Telegram

When you need heavy code/reasoning:
1. Send `/acp spawn codex` — spawns Codex session
2. Work in thread — all messages route to Codex
3. Codex can call arifOS MCP tools via mcporter
4. Close with `/acp close` when done

---

## Configuration

```yaml
acp:
  enabled: true
  dispatch:
    enabled: true  # default
  spawn:
    codex:
      backend: acpx
      mode: persistent
    claude-code:
      backend: acpx
      mode: session
```

---

## Available Harnesses

| Harness | Command | Purpose |
|---------|---------|---------|
| Codex | `/acp spawn codex` | General coding, file operations |
| Claude Code | `/acp spawn claude-code` | Claude CLI with tools |
| Pi | `/acp spawn pi` | Fast inference agent |
| OpenCode | `/acp spawn opencode` | Open-source alternative |
| Gemini CLI | `/acp spawn gemini` | Google Gemini CLI |

---

## Workflow

```
Telegram Message → AGI_bot → (if heavy reasoning)
  → /acp spawn <harness> → arifOS MCP (39 tools)
  → Heavy processing → Return result → Telegram
```

---

**Motto:** "Ditempa bukan diberikan"