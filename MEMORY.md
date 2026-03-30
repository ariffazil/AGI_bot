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