# Quackr MCP Server

Official MCP server for [Quackr](https://quackr.io) — virtual phone numbers for SMS verification and OTP receipt. Use Claude (or any MCP-compatible client) to check pricing and inventory, purchase temporary numbers, and read incoming SMS programmatically.

**Hosted endpoint:** `https://mcp.quackr.io/`
**Transport:** Streamable HTTP
**Auth:** `Authorization: Bearer YOUR_API_KEY` header

## Tools

| Tool | Description |
|---|---|
| `get-balance` | Get the current account balance in USD |
| `get-pricing` | Get phone number rental pricing for a specific country |
| `get-inventory` | Check available phone number inventory for a country |
| `purchase-number` | Purchase a temporary number for receiving SMS (deducts from balance) |
| `check-sms` | Check SMS messages received on a rented number |
| `list-active-numbers` | List all currently active (rented) numbers on the account |

## Getting an API Key

1. Sign in at [quackr.io](https://quackr.io)
2. Open your profile page
3. Copy the API key from the API section

## Claude Code Setup

Add to your `~/.claude.json` (or a project `.mcp.json`):

```json
{
  "mcpServers": {
    "quackr": {
      "type": "http",
      "url": "https://mcp.quackr.io/",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY_HERE"
      }
    }
  }
}
```

Or via the CLI:

```bash
claude mcp add --transport http quackr https://mcp.quackr.io/ --header "Authorization: Bearer YOUR_API_KEY_HERE"
```

## Claude Desktop Setup

Claude Desktop's JSON config only supports local (stdio) servers, so add Quackr as a remote connector instead: **Settings → Connectors → Add custom connector**, enter `https://mcp.quackr.io/`, and add an `Authorization` header with the value `Bearer YOUR_API_KEY`.

## Other MCP Clients

Any client supporting remote Streamable HTTP MCP servers with custom headers works. Point it at `https://mcp.quackr.io/` and pass your key via the `Authorization: Bearer YOUR_API_KEY` header.

## REST API

Quackr also exposes a full REST API at `https://api.quackr.io/` — see [`api.quackr.io/swagger.json`](https://api.quackr.io/swagger.json) for the full spec. Same `x-api-key` auth.

## Support

- Website: [quackr.io](https://quackr.io)
- Issues: file in this repo
- Email: support@quackr.io

## License

MIT — see [LICENSE](LICENSE).
