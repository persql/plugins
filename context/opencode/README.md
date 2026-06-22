# PerSQL Context for OpenCode

Give OpenCode a shared, structured context store, readable by your other agents.

## Setup

```sh
npm install -g @persql/cli
persql login                 # or set PERSQL_TOKEN=psql_live_...
```

Add the MCP server to your `opencode.json` (project or `~/.config/opencode/`):

```json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "persql-context": {
      "type": "local",
      "command": ["persql", "mcp"],
      "enabled": true
    }
  }
}
```

The store is resolved per-repo automatically; use
`"command": ["persql", "mcp", "--scope", "user"]` for a store that follows you
across repos.

## Rule

Add to your `AGENTS.md` so the agent uses the store:

```md
## Shared context (PerSQL)
You have a shared context store via the `persql-context` MCP. On task start,
`recall` what's already known; when you learn a durable fact, `remember` it so
other agents see it. Recall is keyword-based — write facts with searchable words.
```

## Tools

`recall` · `remember` · `remember_raw` · `recent` · `by_tag` · `link` ·
`neighbors` · `forget`.
