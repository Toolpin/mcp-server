# Changelog

Changes to the tool definitions this server publishes.

Toolpin's product is telling people when an MCP server's tools change, so this
file exists to hold Toolpin to the same standard. Every entry can be checked
against the live server:

```
curl "https://toolpin.dev/v1/tools?server=dev.toolpin/toolpin"
```

The hash covers the fields the MCP specification defines for a tool, so a
rewritten description moves it and an internal build stamp does not.

## 2026-08-25

First recorded state. 6 tools.

Server hash `1087c15afc0c94d0`

| Tool | Hash |
| --- | --- |
| `search_servers` | `a830a64750a59226` |
| `get_server` | `1a060cada92d05af` |
| `get_server_tools` | `765f636a4c1990dc` |
| `get_server_changes` | `190d5b02c33c09a1` |
| `get_spec_status` | `0b49736f8bda6d09` |
| `watch_server` | `e007533355fb0e9e` |
