# 05 — MCP Servers (Claude reaches outside the terminal)

**MCP** (Model Context Protocol) lets Claude Code call external services as if they were native tools. With the right MCP servers connected, Claude can:

- Read your Gmail, send drafts.
- Check your calendar, create events.
- Search your Google Drive.
- Open and operate apps on your Mac.
- Browse the web with a real Chrome session.
- Read and write your Obsidian vault via the Obsidian CLI.

This is what turns Claude from "smart REPL" into "actual operating system."

## How to add an MCP server

The general command (varies per server):

```bash
claude mcp add <name> <command...>
```

After adding, restart `claude`. You can list installed servers with:

```bash
claude mcp list
```

## The starter set (in order of usefulness)

### 1. Google Workspace — Gmail, Calendar, Drive

This is the highest-leverage server. Once connected, Claude can read your inbox, draft replies, check your calendar, find documents in Drive.

There are a few options. The most maintained right now (Apr 2026) is:

```bash
# example — check the project's README for the latest install command
claude mcp add google-workspace npx -y @modelcontextprotocol/server-google-workspace
```

It will prompt you for OAuth — log in with the Google account you want Claude to access.

> Tip: use a dedicated Google account (`somil.claude@gmail.com` or similar) if you're not comfortable giving Claude your primary account. You can forward mail and share calendars to the dedicated account.

### 2. GitHub — repos, PRs, issues

If you code, this is essential. Claude can open PRs, comment on issues, read diffs, manage releases.

```bash
claude mcp add github
```

Or use the bundled `gh` CLI (install via `brew install gh && gh auth login`). Claude calls `gh` directly through its bash tool — almost as good as a native MCP server and simpler to set up.

### 3. Obsidian CLI

Lets Claude run vault-aware operations: query notes by tag, find backlinks, refactor properties across many files at once. Install with:

```bash
npm install -g obsidian-cli
# or brew tap obsidian-cli/tap && brew install obsidian-cli
```

Then point Claude at it via MCP or just let Claude shell out to `obsidian` commands.

### 4. Computer use / `claude-in-chrome`

For native macOS apps and browser automation. Claude can take screenshots, click, type, scroll.

Install the Anthropic-provided `claude-in-chrome` extension for browser control. For native apps, use `computer-use` (mac only).

Be careful: these tools are powerful. Default to **read-only** screenshots before giving click/type permission.

### 5. Scheduled tasks

A small MCP server that lets you set up cron-like scheduled prompts. Useful for "every morning, run /daily."

## What you should NOT do

- Don't install 10 MCP servers on day one. Start with Google Workspace + `gh`. Add more only when you hit a real need.
- Don't grant `computer-use` access to apps you don't trust Claude to drive (e.g., banking apps).
- Don't put API keys in your `CLAUDE.md` — keep them in `~/.config/<service>/` or env vars and tell Claude where to find them.

## Permissions

For each MCP tool, the first time Claude tries to use it you'll be prompted to allow/deny. You can pre-approve in `~/.claude/settings.json`:

```json
{
  "permissions": {
    "allow": [
      "mcp__google-workspace__gmail_search",
      "mcp__google-workspace__calendar_list"
    ]
  }
}
```

See [09-hooks.md](09-hooks.md) for more on settings.

Next: [06-skills.md](06-skills.md).
