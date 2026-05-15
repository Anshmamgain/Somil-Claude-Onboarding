# 02 — Install Claude Code

## Prerequisites

- macOS 13+ (Ventura or newer).
- A working terminal (Terminal.app or, better, [iTerm2](https://iterm2.com) or [Warp](https://warp.dev)).
- An active **Claude Pro** subscription.

## Install

Pick one of these:

### Option A — Homebrew (recommended)
```bash
brew install --cask claude-code
```

### Option B — npm
First make sure Node 18+ is installed:
```bash
node --version  # should be >= 18
# if missing or old:
brew install node
```
Then:
```bash
npm install -g @anthropic-ai/claude-code
```

## First login

```bash
claude
```

This opens an authorization flow in your browser. Log in with the same email as your Claude Pro account. Approve. Come back to the terminal.

You should see a prompt like:
```
> _
```

That's the REPL. Type something:
```
who am I and what's the date?
```

It should answer. You're in.

## Useful flags & commands

| Command | What it does |
|---|---|
| `claude` | Start a session in the current folder |
| `claude --resume` | Resume your last session in this folder |
| `claude --model sonnet` | Force a specific model |
| `/help` | List built-in commands |
| `/clear` | Clear conversation context (start fresh) |
| `/exit` | Quit |

## A useful config file

Create `~/.claude/settings.json` if it doesn't exist. You'll add things to it as you go — hooks, permissions, MCP servers. For now, the bare minimum:

```json
{
  "model": "sonnet"
}
```

(Sonnet is the right default on Pro — saves your weekly Opus budget for hard work.)

## Pro vs Max — usage limits

You'll hit a **weekly usage limit** on Pro. To stretch it:

- Default to Sonnet, escalate to Opus only when needed.
- Avoid leaving Claude in a long-running loop while you're AFK.
- Close sessions you're done with (`/exit`).
- Don't keep redundant context around — `/clear` between unrelated tasks.

When the limit hits, you'll see a clear message and a reset timestamp. You can keep using web Claude in the meantime.

## Troubleshooting

- **`claude: command not found`** — restart your shell, or run `hash -r`. If npm-installed, check `npm root -g` is on your `$PATH`.
- **Login loop** — clear cookies for `claude.ai`, try again.
- **Permissions errors when running commands** — Claude will prompt before each command. You can pre-approve common commands in `~/.claude/settings.json` (see [09-hooks.md](09-hooks.md) for permission examples).

Next: [03-obsidian-setup.md](03-obsidian-setup.md).
