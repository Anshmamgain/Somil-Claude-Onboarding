# 07 — Slash Commands

Slash commands are the **fastest path** from "I want to do X" to "X is done."

They're just skills with a friendly name. Type `/<name>` in the REPL, and the matching skill runs.

## How they map to skills

Any skill in `~/.claude/skills/<name>/SKILL.md` is automatically callable as `/<name>`.

So `~/.claude/skills/daily/SKILL.md` → `/daily`.

## The starter set

These are the ones I actually use every week. The onboarding prompt will adapt them to your life:

| Command | Frequency | What it does |
|---|---|---|
| `/daily` | every day | Plan + reflect (evening) or recap (morning) |
| `/weekly` | every Sunday | Project health, what slipped, ONE big thing for next week |
| `/brief` | several times a day | 60-second status — priority, calendar, blockers |
| `/inbox` | every day | Process raw captures in `Inbox/` into the right folders |
| `/learn` | as needed | Capture a book/article/video properly into `Learning/` |
| `/people` | as needed | Update a person's note: last contact, context, follow-up |
| `/goals` | weekly | Review vision → yearly → monthly → weekly cascade |
| `/push` | end of session | `git add . && git commit -m '...' && git push` on the vault |

You don't need all of these on day one. Start with `/daily` and `/brief`. Add the rest when you feel friction.

## Project-scoped slash commands

If you're working in a project that has `<project>/.claude/skills/`, those skills become slash commands only inside that project. Useful for code projects — e.g., `/review` that runs your project's specific code-review checklist.

## A note on naming

Pick short, memorable names. `/daily` beats `/run-daily-review`. You'll be typing these dozens of times a week.

## Hidden slash commands (built-in)

These are always available:

| Command | What it does |
|---|---|
| `/help` | Show built-in commands |
| `/clear` | Clear conversation context |
| `/exit` | Exit |
| `/init` | Bootstrap a project — generates a `CLAUDE.md` |
| `/review` | Code review the current branch |

## Tip: print your commands

Inside Claude Code, type:

```
list every skill I have installed and what each one does
```

Claude reads `~/.claude/skills/`, summarizes, and prints a table. Good way to remember what you've built.

Next: [08-memory-system.md](08-memory-system.md).
