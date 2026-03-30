# ENDPOINTS.md — arifOS Deployment Endpoints

**Version:** 2026.03.30
**Authority:** Muhammad Arif bin Fazil

---

## Live Deployment URLs

| Service | URL | Description |
|---------|-----|-------------|
| **arifOS** | https://arifos.arif-fazil.com/ | Main arifOS platform |
| **arifOS MCP** | https://arifosmcp.arif-fazil.com/ | arifOS MCP Server (11 mega-tools, full kernel) |
| **APEX** | https://apex.arif-fazil.com/ | APEX verdict engine |
| **Personal** | https://arif-fazil.com/ | Personal site |
| **GitHub** | https://github.com/ariffazil/arifosmcp | Source repository |

---

## arifOS MCP Server Details

- **Endpoint:** https://arifosmcp.arif-fazil.com
- **Features:** Local Ollama, Redis, PostgreSQL, Qdrant vector DB
- **Tools:** 11 mega-tools (full kernel)
- **Source:** https://github.com/ariffazil/arifosmcp

## Cloud — Prefect Horizon

- **Repository:** https://github.com/ariffazil/arifOS
- **Entrypoint:** server_horizon.py:mcp
- **URL:** https://arifos.fastmcp.app/mcp
- **Tools:** 8 (proxied to VPS)

---

**Last Updated:** 2026-03-30
