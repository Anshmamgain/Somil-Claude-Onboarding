# 06 — Skills (reusable, named capabilities)

A **skill** is a folder Claude can invoke by name. It contains instructions, optionally scripts, and Claude follows them whenever you trigger the skill. Think of it as a saved prompt with optional code, parameterized for the task.

## Where skills live

```
~/.claude/skills/
├── daily-review/
│   └── SKILL.md
├── weekly-review/
│   └── SKILL.md
└── inbox-process/
    ├── SKILL.md
    └── helpers/
        └── classify.py
```

Each skill folder needs a `SKILL.md` with YAML frontmatter that tells Claude when to use it.

## Anatomy of a `SKILL.md`

```markdown
---
name: daily-review
description: Run an evening planning + morning reflection workflow. Use when the user types /daily or asks for a daily review.
---

# Daily Review

Steps:
1. Read today's daily note at `Daily Notes/<today>.md`. If it doesn't exist, create it from `Templates/daily-note.md`.
2. Read yesterday's note. List anything checked, anything that slipped.
3. Check Google Calendar for today + tomorrow (via mcp__google-workspace__calendar_list).
4. Ask the user 3 questions: ...
5. Update today's note with answers + planned priorities.
```

That's it — a markdown file with instructions. No code required (though you can include scripts).

## How to trigger a skill

Two ways:

1. **By slash command**: typing `/daily-review` in the REPL invokes the matching skill.
2. **By context match**: the `description:` field gets matched against what you're asking. If you say "let's do my daily review," Claude finds and runs the matching skill automatically.

The second mode is the whole point. You shouldn't have to remember command names — you should just describe what you want.

## Three skills you should set up first

The onboarding prompt will scaffold these based on your domains. Generic suggestions:

### `/daily` — evening planning + morning reflection
- Read calendar, daily note, open loops.
- Ask: what's the ONE big thing today, what's slipping, what are you avoiding.
- Update the daily note with priorities.

### `/weekly` — Sunday review
- Aggregate the last 7 daily notes.
- Surface what got done, what slipped.
- Pick the ONE big thing for next week.
- Update each active project's status.

### `/brief` — 60-second status
- Top priority right now.
- Next 3 calendar items.
- Open commitments and their due dates.
- Anything blocked.

## Writing a skill from scratch

The cleanest way: ask Claude.

> "I want a skill called `/learn` that captures a learning item — book, article, podcast. It should prompt me for title, source URL, my one-paragraph takeaway, and save it under `Learning/` with proper frontmatter. Write the SKILL.md at `~/.claude/skills/learn/SKILL.md`."

Claude will write it. Edit if you want, then it's available next session.

## Built-in skills worth knowing

Anthropic ships some default skills. Useful ones:

- `find-docs` — fetch up-to-date official docs for a library or service.
- `defuddle` — extract clean markdown from a webpage (way better than `WebFetch`).
- `obsidian-cli` — wraps obsidian-cli operations.
- `obsidian-markdown` — knows Obsidian-flavored markdown syntax.
- `consolidate-memory` — cleans up your memory files.
- `update-config` — modifies `~/.claude/settings.json` safely.

Use them. Don't rebuild what's already there.

Next: [07-slash-commands.md](07-slash-commands.md).
