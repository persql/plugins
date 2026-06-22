# PerSQL for OpenCode

Give OpenCode its own SQLite database on PerSQL — create tables, run SQL, branch
a sandbox per task, publish endpoints — straight from the agent. The first tool
call runs an OAuth browser flow, so there's **no API key to paste and no account
to create beforehand**.

## Setup

Add the MCP server to your `opencode.json` (project root, or
`~/.config/opencode/opencode.json`):

```json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "persql": {
      "type": "remote",
      "url": "https://mcp.persql.com/mcp",
      "enabled": true
    }
  }
}
```

On first use OpenCode opens your browser to authorize against `persql.com`. Sign
in (GitHub, Google, Apple, or email) and pick the workspace; new accounts get a
primary workspace and a welcome credit. The credential is stored after you
authorize.

If your OpenCode version doesn't yet drive interactive OAuth for remote MCP
servers, mint a workspace token in the console and pass it as a header instead:

```json
{
  "mcp": {
    "persql": {
      "type": "remote",
      "url": "https://mcp.persql.com/mcp",
      "enabled": true,
      "headers": { "Authorization": "Bearer psql_live_..." }
    }
  }
}
```

## What OpenCode can do

Query and `batch` SQL, inspect the schema, create databases, branch a
schema-only sandbox per task, snapshot/restore, scaffold and publish typed HTTP
endpoints, and ask NL→SQL.

## Billing

Usage-only against your workspace's prepaid balance — top up in the console.

## Rule

Add to your `AGENTS.md` so OpenCode reaches for the database when it needs state:

```md
## Database (PerSQL)
You have your own SQLite database via the `persql` MCP. Use it to persist
structured state across turns — create tables, run SQL, branch a sandbox per
task. It's isolated to this workspace.
```
