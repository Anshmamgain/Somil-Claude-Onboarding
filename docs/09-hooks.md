# 09 — Hooks & Automation

Hooks are shell commands the Claude Code **harness** runs in response to events. They run outside the model, so they're guaranteed (the model can't "forget"). Use them to automate the boring parts.

Hooks live in `~/.claude/settings.json` (global) or `<project>/.claude/settings.json` (project).

## Anatomy

```json
{
  "hooks": {
    "session-start": [
      { "command": "echo 'Welcome back, Som.'" }
    ],
    "session-stop": [
      { "command": "git -C ~/Documents/Vault add . && git -C ~/Documents/Vault commit -m 'auto: end-of-session' || true" }
    ]
  }
}
```

Events that fire hooks:

| Event | Fires when |
|---|---|
| `session-start` | A new Claude session begins in this folder |
| `session-stop` | The session ends |
| `prompt-submit` | You hit enter on a prompt |
| `tool-call` | Claude is about to call a tool (can approve/deny) |
| `tool-result` | A tool finished |
| `file-edit` | A file was edited |

(Exact event names may shift between versions — check `claude --help` or `docs.claude.com/claude-code`.)

## Useful hooks to set up

### 1. Auto-commit the vault on session-stop

So you never lose work, and you get a git history of what each session changed.

```json
{
  "hooks": {
    "session-stop": [
      {
        "command": "cd ~/Documents/Vault && git add . && git diff --staged --quiet || git commit -m 'session: $(date +%Y-%m-%d-%H%M)'"
      }
    ]
  }
}
```

### 2. Append a session log to today's daily note

```json
{
  "hooks": {
    "session-stop": [
      {
        "command": "echo '\\n## Session log $(date +%H:%M)\\n- session ended\\n' >> ~/Documents/Vault/Daily\\ Notes/$(date +%Y-%m-%d).md"
      }
    ]
  }
}
```

### 3. Block destructive commands

You can use a `tool-call` hook to require manual confirmation before any `rm -rf`, `git push --force`, etc. Best done via the built-in **permissions** system though:

```json
{
  "permissions": {
    "ask": ["Bash(rm -rf*)", "Bash(git push --force*)"],
    "allow": ["Bash(ls*)", "Bash(cat*)", "Bash(git status*)"]
  }
}
```

## Permissions

The biggest source of friction is Claude asking for permission on every command. Tame it by pre-allowing common safe commands in `~/.claude/settings.json`:

```json
{
  "permissions": {
    "allow": [
      "Bash(ls*)",
      "Bash(cat*)",
      "Bash(head*)",
      "Bash(tail*)",
      "Bash(git status*)",
      "Bash(git diff*)",
      "Bash(git log*)",
      "Bash(rg*)",
      "Bash(grep*)",
      "Bash(fd*)",
      "Bash(find*)",
      "Bash(echo*)",
      "Bash(pwd)",
      "Bash(node --version)",
      "Read(*)",
      "Edit(*)",
      "Write(*)"
    ],
    "ask": [
      "Bash(rm*)",
      "Bash(git push*)",
      "Bash(brew install*)",
      "Bash(npm install*)"
    ]
  }
}
```

You can let Claude itself manage this with the built-in `fewer-permission-prompts` skill — it scans your recent sessions and proposes safe additions.

## Don't over-automate

Hooks are tempting. Resist setting up 20 of them on day one. Two principles:

1. Only automate things you've done **manually at least 5 times** and felt friction.
2. Every hook adds invisible behavior. Document each one in your project `CLAUDE.md`.

You're done with the docs. Read the [../tactics/](../tactics/) folder next for daily-use patterns.
