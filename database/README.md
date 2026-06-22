# PerSQL Database — agent plugins

Give a coding agent **its own SQLite database** on PerSQL, from inside the
agent. Create tables, run SQL, branch a sandbox per task, snapshot, and publish
typed HTTP endpoints — all as MCP tools.

These plugins point the agent at the remote PerSQL MCP server:

```
https://mcp.persql.com/mcp
```

The agent authenticates with **OAuth in the browser** on its first tool call —
this is how a brand-new user signs up: there's no API key to copy and no
account to create first. Sign in (GitHub, Google, Apple, or email), pick a
workspace, and the agent is bound to it. New accounts get a primary workspace
and a welcome credit; the client stores the credential, so it's a one-time step.

| Tool | Config | Setup |
|---|---|---|
| Claude Code | `claude/.claude-plugin/plugin.json` | [claude/README.md](./claude/README.md) |
| Codex | `codex/config.toml` | [codex/README.md](./codex/README.md) |
| OpenCode | `opencode/opencode.json` | [opencode/README.md](./opencode/README.md) |

Any MCP client that supports remote (streamable-HTTP) servers with OAuth works
the same way — point it at `https://mcp.persql.com/mcp`.

In Claude Code you can also install it from the marketplace in this repo:

```sh
/plugin marketplace add persql/plugins
/plugin install persql@persql
```

> Looking for a no-credential way for CI agents (GitHub Actions, Google Cloud,
> GitLab CI) to sign up *without* a human click? That's the federated
> [agent registration](https://docs.persql.com/agents/agent-registration/)
> flow, not these plugins.
