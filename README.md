# FichePro for Claude — MCP Server

[![MCP Registry](https://img.shields.io/badge/MCP%20Registry-io.github.SezerPro%2Ffichepro--mcp-8B5CF6)](https://registry.modelcontextprotocol.io/v0.1/servers?search=fichepro)
[![Protocol](https://img.shields.io/badge/MCP-2025--06--18-10B981)](https://modelcontextprotocol.io/)
[![Website](https://img.shields.io/badge/fichepro.ai-EC4899)](https://fichepro.ai/mcp)

**FichePro for Claude** is a production MCP server for dropshippers and e-commerce operators. It lets your AI assistant generate SEO-optimized product listings, score SEO, audit catalogs, discover niches and suppliers, and surface Autopilot optimizations — directly from your Claude conversation.

This repository hosts the **registry metadata** (`server.json`). The server itself is hosted at **https://www.fichepro.ai/api/mcp**.

## Quick install (Claude Desktop, ~30 seconds)

1. Open **Claude Desktop → Settings → Connectors → Add custom connector**
2. Name: `FichePro`, URL: `https://www.fichepro.ai/api/mcp`
3. Click **Add** → browser opens the FichePro consent screen → log in, pick a workspace, click **Allow**
4. Ask Claude: *"What's my FichePro quota?"*

Full install guide: **https://fichepro.ai/mcp**

## Tools (10)

| Tool | Purpose | Plan |
|---|---|---|
| `generate_product_listing` | SEO-optimized listing across 12 languages × 7 marketplaces | Free* / Starter+ |
| `get_seo_score` | Deterministic 0-100 marketplace SEO score | All |
| `analyze_catalog` | Global catalog audit + prioritized fix list | Starter+ |
| `list_workspaces` | User's accessible workspaces | All |
| `get_quota_status` | Current plan, usage, remaining quota | All |
| `get_autopilot_suggestions` | Optimizations Autopilot would execute tonight | All |
| `generate_ab_test` | Two listing variants (factual vs emotional) | Starter+ |
| `find_niche` | Trending niches with demand/competition scores (Google Trends-backed) | Starter+ |
| `ad_spy_search` | Live Meta Ad Library with winning_score per creative | Starter+ |
| `find_supplier` | AliExpress suppliers with MOQ + margin estimation | Starter+ |

\* Free plan: 1 generation/month via MCP for evaluation.

## Marketplaces supported

Shopify · Amazon · TikTok Shop · Etsy · eBay · WooCommerce · PrestaShop

## Languages supported

fr · en · de · es · it · nl · pt · ar · tr · pl · ja · sv (12 total)

## Authentication

- **OAuth 2.1 with DCR (RFC 7591) + PKCE S256 (RFC 7636)** — native install via Claude Desktop Custom Connectors
- **Bearer API key** — for Cursor, CLI, scripts, CI environments. Generate at https://fichepro.ai/account

Both token families (`fp_live_*` for keys, `fp_oat_*` for OAuth) are accepted on every MCP request.

## Protocol specs

- **MCP version**: `2025-06-18`
- **Transport**: Streamable HTTP (stateless)
- **Rate limit**: 60 requests/minute per token
- **Discovery**:
  - `/.well-known/oauth-authorization-server` (RFC 8414)
  - `/.well-known/oauth-protected-resource` (RFC 9728)

## Links

- **Landing + install guide**: https://fichepro.ai/mcp
- **Account / API keys**: https://fichepro.ai/account
- **MCP Registry entry**: https://registry.modelcontextprotocol.io/v0.1/servers?search=fichepro
- **Contact**: `contact@fichepro.ai`

## License

This repository contains the `server.json` metadata published to the [official MCP Registry](https://registry.modelcontextprotocol.io/). The FichePro server itself is a commercial SaaS; see https://fichepro.ai/terms for the terms of service.

---

*Not affiliated with Anthropic. MCP is an open protocol; Claude is a trademark of Anthropic.*
