# 08 — The Memory System

Claude Code has a built-in, file-based memory system. It's how Claude remembers you across conversations.

## Where it lives

```
~/.claude/projects/<slugified-folder-path>/memory/
├── MEMORY.md           ← the index, always loaded into context
├── user_role.md
├── feedback_tone.md
├── project_<thing>.md
└── reference_<thing>.md
```

Each project (= each working directory you open Claude in) has its own memory folder. So memory for your vault lives at:

```
~/.claude/projects/-Users-somil-Documents-Vault/memory/
```

(Path is auto-derived from the folder location.)

## The four memory types

| Type | What goes here | Example |
|---|---|---|
| **user** | Who you are, your role, preferences, expertise | "Somil is a product manager at X, 6 years experience" |
| **feedback** | How you want Claude to behave — corrections AND validations | "Be blunt, no fluff. Don't ask before checking — just check." |
| **project** | State of ongoing work, who/what/why, not derivable from code | "Q3 goal is shipping X by Sep 30, blocked on Y" |
| **reference** | Pointers to where info lives in other systems | "Bugs tracked in Linear project ABC" |

## How memory gets written

You don't write it manually (usually). Claude writes it when:

- You explicitly say "remember that..." or "save this preference."
- You correct Claude and it should generalize.
- You confirm a non-obvious choice ("yeah, that approach was right").
- You teach Claude something durable about you.

You can also write entries manually. Each file looks like:

```markdown
---
name: feedback_tone
description: How Somil wants to be addressed and the response style he prefers
type: feedback
---

Address Somil as "Som". Be blunt — no preamble, no "great question." Have an opinion.

**Why:** Som's an operator, not a learner; he doesn't want options, he wants a recommendation.
**How to apply:** Default to one-line answers + a take. Expand only if asked.
```

And `MEMORY.md` is the index:

```markdown
- [Tone](feedback_tone.md) — Be blunt, address as "Som"
- [Role](user_role.md) — Product manager at X
```

`MEMORY.md` is always loaded into context. Individual files are only loaded when relevant.

## What NOT to put in memory

- Code patterns (Claude can read the code)
- Git history (Claude can run `git log`)
- Current task state (use TODOs, not memory)
- Things already in your `CLAUDE.md`

Memory is for **across-session** facts. Per-session state goes elsewhere.

## How memory affects Claude's behavior

When you start a new session in your vault, Claude:

1. Loads global `~/.claude/CLAUDE.md`.
2. Loads project `<vault>/CLAUDE.md`.
3. Loads `<vault>/memory/MEMORY.md` (index).
4. Pulls individual memory files when their description matches what you're doing.

So memory makes Claude **more like you** over time. After a month of regular use, a fresh session already knows your tone, your projects, your people, your preferences.

## Inspecting memory

```bash
ls ~/.claude/projects/-Users-somil-Documents-Vault/memory/
cat ~/.claude/projects/-Users-somil-Documents-Vault/memory/MEMORY.md
```

Or just ask:

> "List all your memory entries about me. Group by type."

## Cleaning memory

Memories drift. The `consolidate-memory` skill (built-in) does a reflective pass: merges duplicates, fixes stale facts, prunes the index. Run it every couple of months:

```
/consolidate-memory
```

Next: [09-hooks.md](09-hooks.md).
