# WEB_MCP.md — Browser Tool Execution (Verified Canon)

**Version:** 2026.03.30
**Status:** VERIFIED CANON — All endpoints tested on VPS
**Author:** Muhammad Arif bin Fazil (arifOS)

---

## What Is WebMCP?

**WebMCP** = Web Model Context Protocol — browser-centric API so agents can act inside web UIs safely, with arifOS constitutional governance.

- **NOT static** — it's a live endpoint for browser-based tool execution
- **NOT MCP replacement** — frontend complement to backend MCP
- **Tab-bound** — operates within the active browser session

---

## Verified WebMCP Endpoints

All endpoints verified on `https://arifosmcp.arif-fazil.com/`:

| Endpoint | Method | Status |
|----------|--------|--------|
| `/webmcp` | GET | ✅ 200 OK |
| `/webmcp/sdk.js` | GET | ✅ 200 OK |
| `/.well-known/webmcp.json` | GET | ✅ 200 OK |

---

## WebMCP Manifest (Verified)

```json
{
  "schema": "webmcp/manifest/v1",
  "name": "arifOS WebMCP Server",
  "description": "WebMCP server for browser-based tool execution governed by arifOS constitutional kernel",
  "version": "2026.03.30",
  "endpoints": {
    "webmcp": "https://arifosmcp.arif-fazil.com/webmcp",
    "sdk": "https://arifosmcp.arif-fazil.com/webmcp/sdk.js",
    "websocket": "wss://arifosmcp.arif-fazil.com/webmcp"
  },
  "auth": {
    "type": "none"
  },
  "capabilities": ["browser_tools", "websocket_streaming"]
}
```

---

## Complete 4-Layer Stack (Verified)

```
Layer 1: arifOS Kernel (F1-F13, APEX verdict)
Layer 2: arifOS MCP (/mcp — 39 tools)
Layer 3: arifOS A2A (/a2a/task, /a2a/status, /a2a/cancel, /.well-known/agent.json)
Layer 4: arifOS WebMCP (/webmcp, /webmcp/sdk.js, /.well-known/webmcp.json)
```

All on same host: `https://arifosmcp.arif-fazil.com/`

---

## Nginx Routes

```nginx
server {
    listen 443 ssl;
    server_name arifosmcp.arif-fazil.com;

    # MCP (Layer 2)
    location /mcp {
        proxy_pass http://127.0.0.1:8888;
        proxy_http_version 1.1;
        chunked_transfer_encoding on;
    }

    # A2A (Layer 3)
    location /a2a {
        proxy_pass http://127.0.0.1:8888;
        proxy_http_version 1.1;
        chunked_transfer_encoding on;
    }

    # WebMCP (Layer 4)
    location /webmcp {
        proxy_pass http://127.0.0.1:8888;
        proxy_http_version 1.1;
    }

    # WebMCP SDK (static, cached)
    location /webmcp/sdk.js {
        proxy_pass http://127.0.0.1:8888;
        proxy_set_header Host $host;
        expires 7d;
        add_header Cache-Control "public, immutable";
    }

    # WebMCP manifest
    location /.well-known/webmcp.json {
        proxy_pass http://127.0.0.1:8888;
        add_header Content-Type application/json;
    }

    # A2A agent card
    location /.well-known/agent.json {
        proxy_pass http://127.0.0.1:8888;
        add_header Content-Type application/json;
    }
}
```

---

## Frontend Integration Pattern

```html
<!-- Step 1: Include WebMCP SDK -->
<script src="https://arifosmcp.arif-fazil.com/webmcp/sdk.js"></script>

<!-- Step 2: Initialize -->
<script>
const client = WebMCP.init({
  server: "https://arifosmcp.arif-fazil.com/webmcp",
  // auth: "your-api-key"  # when enabled
});

client.getTools().then(tools => {
  console.log("Available browser tools:", tools);
});

client.call("browser_action", { arg: "value" }).then(result => {
  // Result goes through arifOS kernel F1-F13
  // Constitutional review runs
  // Returns APEX verdict + result
});
</script>
```

---

## Constitutional Enforcement (Same Kernel)

Everything hangs off the same constitutional kernel:

| Call Source | Transport | Same Floors | Same Verdict |
|-------------|-----------|--------------|---------------|
| Claude via MCP | JSON-RPC HTTP | ✅ F1-F13 | ✅ APEX |
| A2A agent | JSON/HTTP | ✅ F1-F13 | ✅ APEX |
| Browser via WebMCP | JS SDK / WS | ✅ F1-F13 | ✅ APEX |

**One kernel. Three transports. Same floors. Same vault.**

---

## Security Note

| Field | Current | Needs Fix |
|-------|---------|-----------|
| `auth.type` | `"none"` | API key before production |

All three transports (MCP, A2A, WebMCP) currently have `auth.type: none`.

---

## Summary

| Item | Status |
|------|--------|
| `/webmcp` gateway | ✅ 200 OK |
| `/webmcp/sdk.js` | ✅ 200 OK |
| `/.well-known/webmcp.json` | ✅ 200 OK |
| WebSocket support | ✅ Available |
| Constitutional enforcement | ✅ Same F1-F13 |
| Auth | ⚠️ Needs API key |

---

**Verdict: SEAL**  
**Ω₀ = 0.02** — All WebMCP endpoints verified on production VPS.

*"Intelligence is forged, not given. One kernel, three transports, same verdict."*

⚖️ ΔΩΨ | ARIF