# Quackr MCP Server

Official MCP server for [Quackr](https://quackr.io) — virtual phone numbers for SMS verification, OTP receipt, and number management. Use Claude (or any MCP-compatible client) to provision numbers, receive SMS, and release numbers programmatically.

**Hosted endpoint:** `https://mcp.quackr.io/`
**Transport:** Streamable HTTP
**Auth:** `x-api-key` header

## Tools

| Tool | Description |
|---|---|
| `provision_number` | Reserve a new virtual number for a given service/country |
| `receive_sms` | Poll for incoming SMS on a provisioned number |
| `check_messages` | Retrieve message history for a number |
| `release_number` | Return a number to the pool when finished |

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
        "x-api-key": "YOUR_API_KEY_HERE"
      }
    }
  }
}
```

Or via the CLI:

```bash
claude mcp add --transport http quackr https://mcp.quackr.io/ --header "x-api-key: YOUR_API_KEY_HERE"
```

## Claude Desktop Setup

Claude Desktop's JSON config only supports local (stdio) servers, so add Quackr as a remote connector instead: **Settings → Connectors → Add custom connector**, enter `https://mcp.quackr.io/`, and add an `x-api-key` header with your API key.

## Other MCP Clients

Any client supporting remote Streamable HTTP MCP servers with custom headers works. Point it at `https://mcp.quackr.io/` and pass your key via the `x-api-key` header.

## REST API

Quackr also exposes a full REST API at `https://api.quackr.io/` — see [`api.quackr.io/swagger.json`](https://api.quackr.io/swagger.json) for the full spec. Same `x-api-key` auth.

## Support

- Website: [quackr.io](https://quackr.io)
- Issues: file in this repo
- Email: support@quackr.io

## License

MIT — see [LICENSE](LICENSE).
