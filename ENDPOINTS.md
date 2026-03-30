# ENDPOINTS.md — arifOS Deployment Endpoints

**Version:** 2026.03.30
**Authority:** Muhammad Arif bin Fazil
**Last Checked:** 2026-03-30T03:53Z

---

## Live Deployment URLs

| Service | URL | Status | Notes |
|---------|-----|--------|-------|
| **arifOS** | https://arifos.arif-fazil.com/ | ✅ 200 | Main platform |
| **arifOS MCP** | https://arifosmcp.arif-fazil.com/ | ✅ 200 | Full kernel (11 tools) |
| **APEX** | https://apex.arif-fazil.com/ | ✅ 301→200 | Redirects to /docs/apex-theory.html |
| **Personal** | https://arif-fazil.com/ | ✅ 200 | Personal site |
| **Horizon (cloud)** | https://arifos.fastmcp.app/mcp | ❌ 404 | Cloud MCP — not deployed yet |
| **GitHub arifosmcp** | https://github.com/ariffazil/arifosmcp | ✅ 200 | Source repository |

---

## GitHub Repositories

| Repo | URL | Status |
|------|-----|--------|
| **arifOS** | https://github.com/ariffazil/arifOS | ✅ 200 |
| **APEX** | https://github.com/ariffazil/APEX | ✅ 200 |
| **GEOX** | https://github.com/ariffazil/GEOX | ✅ 200 |
| **arif-sites** | https://github.com/ariffazil/arif-sites | ✅ 200 |
| **ariffazil** | https://github.com/ariffazil/ariffazil | ✅ 200 |
| **AGI_bot** | https://github.com/ariffazil/AGI_bot | ✅ 200 |

---

## arifOS MCP Server Details

**VPS — Sovereign Deployment:**
- **URL:** https://arifosmcp.arif-fazil.com
- **Tools:** 11 mega-tools (full kernel)
- **Features:** Local Ollama, Redis, PostgreSQL, Qdrant vector DB
- **Source:** https://github.com/ariffazil/arifosmcp

**Cloud — Prefect Horizon:**
- **URL:** https://arifos.fastmcp.app/mcp
- **Status:** ❌ 404 (not deployed)
- **Tools:** 8 (proxied to VPS when active)

---

## APEX Redirect

`https://apex.arif-fazil.com/` → redirects to → `https://arifos.arif-fazil.com/docs/apex-theory.html`

---

## Summary

- **Operational:** 5/6 web services + 6/6 GitHub repos
- **Not Ready:** Horizon cloud MCP (404)
- **Action Item:** Deploy to Horizon or update URL when ready

---

**Last Updated:** 2026-03-30T03:53Z