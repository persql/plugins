# PerSQL — editor & agent plugins

Thin pointers that wire a coding agent into PerSQL. Two products, two folders:

- **[`database/`](./database/)** — give the agent **its own SQLite database**
  (create tables, run SQL, branch a sandbox, publish endpoints). Points at the
  remote `mcp.persql.com` server; the agent signs in (or signs up) via OAuth in
  the browser on first use — no API key to copy.
- **[`context/`](./context/)** — give the agent a **shared, structured context
  store** so memory follows you across Claude Code, OpenCode, Codex, and cloud.
  Runs through the local `persql mcp` stdio shim after `persql login`.

| Product | Claude Code | Codex | OpenCode |
|---|---|---|---|
| Database | [database/claude](./database/claude/) | [database/codex](./database/codex/) | [database/opencode](./database/opencode/) |
| Context | [context/claude](./context/claude/) | [context/codex](./context/codex/) | [context/opencode](./context/opencode/) |

## Database (`database/`)

```sh
# Claude Code
claude mcp add --transport http persql https://mcp.persql.com/mcp
# Codex
codex mcp add persql --url https://mcp.persql.com/mcp
# OpenCode — add the block from database/opencode/opencode.json
```

In Claude Code you can also install from the marketplace this repo defines:

```sh
/plugin marketplace add persql/plugins
/plugin install persql@persql            # database
/plugin install persql-context@persql    # shared context (needs the persql CLI)
```

The first tool call opens the browser to authorize. A brand-new user signs up
right there and gets a primary workspace with a welcome credit; the client
stores the credential, so it's a one-time step.

## Context (`context/`)

```sh
npm install -g @persql/cli
persql login          # once
persql mcp            # stdio MCP server, proxies to context.persql.com
```

`persql mcp` resolves the context store automatically — **per-repo** (default,
keyed on the git `origin` remote) or **user-global** (`persql mcp --scope user`).
It injects the resolved store into every call, so the agent can't address the
wrong one. Set `PERSQL_TOKEN` to a namespace token (`psql_live_…`).

Each context plugin also ships a short rule telling the agent to **recall before
starting and remember durable facts as it learns them**.
