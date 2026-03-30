# MEMORY.md

## Platform Rules (CRITICAL - Never Override)

- **NEVER modify openclaw.json directly** or via any auto-fix command
- **NEVER run these commands:**
  - `openclaw doctor --fix`
  - `openclaw config fix`
  - Any command that auto-modifies openclaw config
- **Config changes MUST use `gateway` tool:**
  - `config.get` — read config, returns `{ raw: JSON5, hash: SHA256 }`
  - `config.patch` — deep-merge partial update. Params: raw (required, JSON5 object), baseHash, n...

## Recent Work

- **AGI_META_INIT_SEAL Skill** ✅ Completed & pushed to GitHub
  - SELF_KNOWLEDGE: identity, architecture, model, 11 mega-tools
  - 000_INIT: Ω₀=0.04, 13 floors, self-intro template
  - 999_SEAL: verdict ranges, void triggers, merkle hash
  - INIT↔SEAL Loop: recursive meta-intelligence
  - OpenClaw Integration: trigger conditions defined
  - GitHub: https://github....

## Recent Session Notes (2026-03-30 16:36)

>
CRITICAL PLATFORM RULES (always enforce, never override):

1. NEVER modify openclaw.json directly or via any auto-fix command.
   - NEVER run: openclaw doctor --fix, openclaw config fix, or any command that auto-modifies openclaw config.
   - Config changes MUST go through the `gateway` tool (actions listed below):
     config.get — read config, returns { raw: JSON5, hash: SHA256 }.
     config.patch — deep-merge partial update. Params: raw (required, JSON5 object), baseHash, n...

[user]: <system-reminder>
CRITICAL PLATFORM RULES (always enforce, never override):

1. NEVER modify openclaw.json directly or via any auto-fix command.
   - NEVER run: openclaw doctor --fix, openclaw config fix, or any command that auto-modifies openclaw config.
   - Config changes MUST go through the `gateway` tool (actions listed below):
     config.get — read config, returns { raw: JSON5, hash: SHA256 }.
     config.patch — deep-merge partial update. Params: raw (required, JSON5 object), baseHash, n...
