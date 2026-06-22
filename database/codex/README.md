# PerSQL for Codex

Give the Codex CLI its own SQLite database on PerSQL. The first tool call runs
an OAuth browser flow — sign in or sign up and pick a workspace — so there's
**no API key to paste and no account to create beforehand**.

## Setup

```sh
codex mcp add persql --url https://mcp.persql.com/mcp
```

Or add the block from [`config.toml`](./config.toml) to `~/.codex/config.toml`.

On first use Codex opens your browser to authorize against `persql.com`. Sign
in (GitHub, Google, Apple, or email) and choose the workspace; new accounts get
a primary workspace and a welcome credit. Codex stores the credential after you
authorize.

If your Codex version needs it for remote servers, set the top-level
`experimental_use_rmcp_client = true` in `config.toml`. A fixed OAuth callback
port can be pinned with `mcp_oauth_callback_port`.

## What Codex can do

Query and `batch` SQL, inspect the schema, create databases, branch a
schema-only sandbox per task, snapshot/restore, scaffold and publish typed HTTP
endpoints, and ask NL→SQL.

## Billing

Usage-only against your workspace's prepaid balance — top up in the console.

## Rule

Add to your `AGENTS.md` so Codex reaches for the database when it needs state:

```md
## Database (PerSQL)
You have your own SQLite database via the `persql` MCP. Use it to persist
structured state across turns — create tables, run SQL, branch a sandbox per
task. It's isolated to this workspace.
```
