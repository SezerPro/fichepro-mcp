# FichePro for Claude: MCP server

[![MCP Registry](https://img.shields.io/badge/MCP%20Registry-io.github.SezerPro%2Ffichepro--mcp-8B5CF6)](https://registry.modelcontextprotocol.io/v0.1/servers?search=fichepro)
[![Protocol](https://img.shields.io/badge/MCP-2025--06--18-10B981)](https://modelcontextprotocol.io/)
[![Website](https://img.shields.io/badge/fichepro.ai-EC4899)](https://www.fichepro.ai/mcp)

FichePro AI writes product listings for online sellers from the facts the seller provides: SEO title, hook, bullet points, short and long descriptions, answers to buyer objections, meta title and description, URL slug and tags, with a rule-based SEO score out of 100. It works only from the facts given and marks missing information as not provided.

This MCP server lets Claude, or any MCP client, use FichePro in your workspace: write and score listings, audit your catalog, and run FichePro's research tools.

This repository hosts the registry metadata (`server.json`). The server itself runs at **https://www.fichepro.ai/api/mcp**.

## Install in Claude

On the web or in the desktop app, on every Claude plan (Claude's Free plan allows one custom connector).

1. In Claude, go to **Customize > Connectors** and click **Add custom connector**.
2. Enter the server URL `https://www.fichepro.ai/api/mcp` (name it `FichePro` if asked). No OAuth client ID is needed: Claude registers itself automatically.
3. Click **Add**, then connect: FichePro opens. Sign in, choose a workspace, then click **Allow**.
4. Ask Claude: *"What's my FichePro quota?"*

On Claude Team and Enterprise plans, an Owner adds the connector in **Organization settings > Connectors**; members then connect from **Customize > Connectors**.

Other MCP clients (Cursor, scripts, CI): create an API key at https://www.fichepro.ai/account/api and send it as `Authorization: Bearer fp_live_…`.

Install guide: https://www.fichepro.ai/mcp

## Tools

The server is open on every plan, Free included. Each tool applies the quotas of your plan: https://www.fichepro.ai/pricing

| Tool | What it does | From plan |
|---|---|---|
| `generate_product_listing` | Writes a listing for one marketplace from your product facts, with its SEO score | Free |
| `get_seo_score` | Rule-based SEO score (0-100) of a listing for a marketplace, criterion by criterion, with tips | Free |
| `get_quota_status` | Your plan, listings used this month, listings left and the reset date | Free |
| `list_workspaces` | The workspaces you can access | Free |
| `get_autopilot_suggestions` | What Autopilot would change in your listings, and why. Autopilot does not run yet: this tool only lists suggestions | Free |
| `analyze_catalog` | SEO health of your catalog: overall score, breakdown by marketplace, listings to fix | Starter |
| `generate_ab_test` | Two versions of a listing with two angles (factual, emotional), for you to compare. Uses 2 listings from your quota | Starter |
| `simulate_buyer_personas` | 10 simulated buyers react to a listing: verdicts, objections, price reaction | Starter |
| `run_multi_agent_campaign` | A launch package for one product: listing, SEO, up to 3 AI illustrations, buyer objections and ad texts to review. Uses 1 listing from your quota; nothing is posted | Starter |
| `find_niche` | Niche ideas and related keywords for a market term | Starter |
| `ad_spy_search` | Searches the Meta Ad Library for ads matching a keyword and a country | Starter |
| `find_supplier` | Sourcing options for a product: a hand-verified directory of sourcing platforms, plus AliExpress prices as a benchmark when they can be read | Starter |
| `predict_winning_products` | Scores the momentum of up to 20 products from public-data signals; an unavailable signal is flagged, never filled in | Pro |

The tools write and score listings. None of them publishes to a marketplace.

## Marketplaces and languages

- Listing formats: Shopify, Amazon, TikTok Shop, Etsy, eBay, WooCommerce, PrestaShop.
- 10 listing languages: French, English, German, Spanish, Italian, Dutch and Turkish on every plan; Portuguese, Arabic and Japanese from the Pro plan.

## Authentication

- **OAuth 2.1** with dynamic client registration (RFC 7591) and PKCE S256 (RFC 7636): the Claude connector flow above. Access tokens start with `fp_oat_`.
- **API key** (`fp_live_…`) as a Bearer token, for other clients.
- Discovery: `/.well-known/oauth-authorization-server` (RFC 8414) and `/.well-known/oauth-protected-resource` (RFC 9728).

## Protocol

- MCP version `2025-06-18`, JSON-RPC 2.0 over Streamable HTTP.
- Rate limit: 60 requests per minute per token, shared across tools.

## Links

- Install guide: https://www.fichepro.ai/mcp
- API keys: https://www.fichepro.ai/account/api
- Pricing and quotas: https://www.fichepro.ai/pricing
- Privacy policy: https://www.fichepro.ai/privacy
- Terms of service: https://www.fichepro.ai/terms
- MCP Registry entry: https://registry.modelcontextprotocol.io/v0.1/servers?search=fichepro
- Contact: `contact@fichepro.ai`

## License

This repository contains the `server.json` metadata published to the [official MCP Registry](https://registry.modelcontextprotocol.io/). The FichePro server itself is a commercial SaaS; see https://www.fichepro.ai/terms for the terms of service.

---

*Not affiliated with Anthropic. MCP is an open protocol; Claude is a trademark of Anthropic.*
