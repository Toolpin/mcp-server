# Toolpin MCP server

An MCP server that answers questions about **other MCP servers**: whether one
answered when we last probed it, what its tools claimed to do, and whether that
claim has changed since.

Useful when an agent is choosing which server to depend on, and useful in the
moment something breaks and you want to know whether the tools moved under you.

**`https://toolpin.dev/mcp`** &nbsp; Streamable HTTP, stateless, no sign-up.

```json
{
  "mcpServers": {
    "toolpin": {
      "url": "https://toolpin.dev/mcp"
    }
  }
}
```

## Tools

| Tool | What it answers |
| --- | --- |
| `search_servers` | Find MCP servers in the public registry by name or title. |
| `get_server` | Everything Toolpin has observed about one MCP server: reachability of each remote endpoint and when each was last checked and last verified, repository activity, the current tool-definition hash, and how many changes it has recorded in the last 90 days. |
| `get_server_tools` | The tool definitions one MCP server advertised when Toolpin last read them, each with a SHA-256 hash of the fields the MCP specification defines. |
| `get_server_changes` | Changes Toolpin recorded for one MCP server: tool definitions changing, and endpoints going down or coming back. |
| `get_spec_status` | The current MCP specification revision, which of its proposals Toolpin checks for, and how much of the catalog has migrated. |
| `watch_server` | Start monitoring an MCP server on the caller's Toolpin account, so they are emailed when it changes or stops answering. |

Full parameters and response shapes: <https://toolpin.dev/api>, or the
machine-readable schema at <https://toolpin.dev/openapi.json>.

## Limits

No key needed to read. Add one as an `Authorization: Bearer` header to raise the
limit, and to use `watch_server`, which acts on your account.

| Caller | Distinct servers per day |
| --- | --- |
| Anonymous | 25 |
| Signed in, free | 200 |
| Any paid plan | Unmetered |

The limit counts **distinct servers**, not requests. Asking about the same
servers all day costs one against the limit each, however often you ask, so
watching your own dependencies never runs out. Never put a key in a URL.

## What it will not tell you

No score, no grade, no rating, no safety judgment. Tool descriptions and
annotations are reproduced exactly as the server published them: they are claims
by that server's author, not anything Toolpin verified. A tool whose annotations
say it only reads may do anything at all.

What Toolpin can tell you is whether the claim changed, because it hashes the
fields the MCP specification defines and compares them daily. That is the whole
product.

Methodology: <https://toolpin.dev/methodology>

## This repository

Documentation and the published registry manifest. The service itself is closed
source. Tool-definition changes are recorded in [CHANGELOG.md](CHANGELOG.md),
which is the same thing Toolpin watches for on everyone else.

Questions: <hello@toolpin.dev>
