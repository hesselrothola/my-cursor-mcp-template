# Claude MCP Project Template (Cursor + VS Code · Claude Code + Codex)

This template now works in Cursor **and** VS Code regardless of which Anthropic coding agent you prefer—Claude Code or Codex. Both agents can load the same setup prompts and MCP configuration so your tooling stays in sync across editors.

## Setup

### 0. Create a new project from this template
1. On GitHub, click **“Use this template”** on the [my-fullstack-template](../) repo and create your new repository.
2. Clone the new repo in your preferred editor:
   - **Cursor (Claude Code or Codex):** `File → Open Workspace` and select the repo.
   - **VS Code (Claude Code or Codex extension):** `File → Open Folder…` and pick the repo directory.

---

### 1. First-time on a new laptop (per machine)
Open the chat/composer for Claude Code or Codex inside your IDE and run the prompt from **“MCP Setup & Health Check (New Laptop)”**.

The automation will:
- Check if all required MCP servers and Playwright are installed.
- Install anything missing.
- Run a quick health check across Context7, SQLite, OpenAPI, Playwright, and Postgres MCPs.

Do this **once per laptop** regardless of the IDE you use.

---

### 2. Daily development (per project)
Whenever you start working on a project created from this template, run the prompt from **“Project MCP Setup & Usage Prompt”** inside Cursor or VS Code (with either Claude Code or Codex).

It will:
- Load `.env` and `.context/claude.md`.
- Ensure the required MCP servers are running.
- Perform health checks.
- Apply the project rules (unified diffs, tests, guardrails).

---

That’s it — after this, you’re ready to build 🚀

## Registering MCP servers in your IDE

All environments share the same MCP endpoints; only the configuration syntax changes. Configure both agents so you can switch between Claude Code and Codex without re-editing files.

### Cursor (Claude Code or Codex)
Add or merge the following into `~/.cursor/settings.json`:

```json
{
  "mcpServers": {
    "context7":  { "type": "http",  "url": "http://127.0.0.1:${CONTEXT7_PORT}" },
    "playwright":{ "type": "stdio", "command": "npx", "args": ["@playwright/mcp@latest"] },
    "postgres":  { "type": "http",  "url": "http://127.0.0.1:${POSTGRES_PORT}" },
    "sqlite":    { "type": "http",  "url": "http://127.0.0.1:${SQLITE_PORT}" },
    "openapi":   { "type": "http",  "url": "http://127.0.0.1:${OPENAPI_PORT}" }
  }
}
```

### VS Code — Claude Code extension
Open the VS Code **Settings (JSON)** view and add:

```json
{
  "claude.mcpServers": {
    "context7":  { "type": "http",  "url": "http://127.0.0.1:${CONTEXT7_PORT}" },
    "playwright":{ "type": "stdio", "command": "npx", "args": ["@playwright/mcp@latest"] },
    "postgres":  { "type": "http",  "url": "http://127.0.0.1:${POSTGRES_PORT}" },
    "sqlite":    { "type": "http",  "url": "http://127.0.0.1:${SQLITE_PORT}" },
    "openapi":   { "type": "http",  "url": "http://127.0.0.1:${OPENAPI_PORT}" }
  }
}
```

VS Code automatically merges this with any existing Claude Code extension settings.

### VS Code — Codex extension
If you also use the Codex extension, mirror the same configuration under the `codex.mcpServers` key:

```json
{
  "codex.mcpServers": {
    "context7":  { "type": "http",  "url": "http://127.0.0.1:${CONTEXT7_PORT}" },
    "playwright":{ "type": "stdio", "command": "npx", "args": ["@playwright/mcp@latest"] },
    "postgres":  { "type": "http",  "url": "http://127.0.0.1:${POSTGRES_PORT}" },
    "sqlite":    { "type": "http",  "url": "http://127.0.0.1:${SQLITE_PORT}" },
    "openapi":   { "type": "http",  "url": "http://127.0.0.1:${OPENAPI_PORT}" }
  }
}
```

Now both Claude Code and Codex are ready to consume your MCPs in either editor.

## MCP Reference

- **Context7 MCP** — Pulls up-to-date, version-specific documentation and code examples straight from the source, placing them directly into your prompt.
- **Postgres MCP** — Lets your IDE query the Postgres database (read-only by default).
- **SQLite MCP** — Lets your IDE query a local SQLite database file.
- **OpenAPI MCP** — Lets your IDE call APIs defined by an OpenAPI spec.
- **Playwright MCP** — Enables end-to-end browser tests and UI automation.

