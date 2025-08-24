# New Cursor and Claude Code Project (MCP-enabled)

## Setup

### 0. Create a new project from this template
On GitHub, click **“Use this template”** on the [my-fullstack-template](../) repo and create a new repository.  
Then open Cursor → clone the new repo into your workspace.  

---

### 1. First-time on a new laptop
If this is your first time using MCPs on this machine:  
In Cursor chat, copy the text from **“MCP Setup & Health Check (New Laptop)”** and paste it.  

Cursor will:  
- Check if all required MCP servers and Playwright are installed  
- Install anything missing  
- Run a quick health check  

Do this **once per laptop**.

---

### 2. Daily development (per project)
For every new project created from this template:  
In Cursor chat, copy the text from **“Project MCP Setup & Usage Prompt”** and paste it.  

Cursor will:  
- Load `.env` and `.context/claude.md`  
- Ensure MCP servers are running  
- Run health checks  
- Apply coding rules (unified diffs, tests, guardrails)  

---

That’s it — after this, you’re ready to build 🚀

## MCP Reference

- **Context7 MCP** → Injects project rules and style guides from `.context/claude.md`.  
- **Postgres MCP** → Lets Cursor run read-only queries against a Postgres database.  
- **SQLite MCP** → Same as Postgres MCP, but for local SQLite databases.  
- **OpenAPI MCP** → Lets Cursor call external APIs from an OpenAPI specification.  
- **Playwright MCP** → Enables Cursor to run end-to-end browser tests and automate UIs. 
