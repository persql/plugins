# PerSQL for Claude Code

Give Claude Code its own SQLite database on PerSQL — create tables, run SQL,
branch a sandbox, publish endpoints — straight from chat. The first tool call
opens your browser to sign in; a brand-new account and workspace are
provisioned right there. **No API key to copy, no sign-up form to fill first.**

## Setup

One command:

```sh
claude mcp add --transport http persql https://mcp.persql.com/mcp
```

The first time Claude uses a `persql` tool, Claude Code opens a browser to
`persql.com` to authorize. Sign in (or sign up — GitHub, Google, Apple, or
email) and pick the workspace the agent should use. New accounts get a primary
workspace and a welcome credit automatically; the token is stored by Claude
Code, so you only do this once.

Or install as a plugin (this folder is a Claude Code plugin — `.claude-plugin/plugin.json`
wires the same remote server), then everyone who installs it gets the tools
without running the command.

## What Claude can do

Query and `batch` SQL, inspect the schema, create databases, branch a
schema-only sandbox per task, snapshot/restore, scaffold and publish typed
HTTP endpoints, and ask NL→SQL. See the full tool list at
[mcp.persql.com](https://mcp.persql.com) / the docs.

## Billing

Usage-only against your workspace's prepaid balance — top up in the console.
There's nothing to configure here; the OAuth flow binds the agent to the
workspace you pick.
