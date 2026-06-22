# PerSQL Context for Claude Code

Give Claude Code a shared, structured context store. Anything it remembers is
visible to your other agents (OpenCode, Codex, cloud) and future sessions.

## Setup

```sh
npm install -g @persql/cli       # provides the `persql` binary
persql login                     # or set PERSQL_TOKEN=psql_live_...
claude mcp add persql-context -- persql mcp
```

Or commit `.mcp.json` (in this folder) to your repo root so the whole team
gets it:

```json
{
  "mcpServers": {
    "persql-context": { "command": "persql", "args": ["mcp"] }
  }
}
```

The store is resolved per-repo automatically. For a store that follows you
across repos, use `"args": ["mcp", "--scope", "user"]`.

## Tools

`recall` · `remember` · `remember_raw` · `recent` · `by_tag` · `link` ·
`neighbors` · `forget`.

## Rule

Add this to your `CLAUDE.md` so Claude uses the store without being asked:

```md
## Shared context (PerSQL)
You have a shared context store via the `persql-context` MCP. On task start,
`recall` what's already known about this project. When you learn a durable
fact — a decision, convention, constraint, or identifier — `remember` it so
other agents and future sessions see it. Recall is keyword-based; write facts
with the words you'd later search.
```

## Slash commands

Copy `commands/recall.md` and `commands/remember.md` into your project's
`.claude/commands/` for `/recall` and `/remember`.
