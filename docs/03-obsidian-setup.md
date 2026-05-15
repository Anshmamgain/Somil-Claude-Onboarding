# 03 — Obsidian as Claude's Brain

[Obsidian](https://obsidian.md) is a free, local-first markdown editor. Notes are plain `.md` files on disk. **That's the killer feature** — because they're plain files, Claude Code can read and write them directly.

This means: your notes, your projects, your daily log, your contacts, your goals — Claude sees all of it.

## Why Obsidian (vs Notion, Apple Notes, etc.)

| | Obsidian | Notion | Apple Notes |
|---|---|---|---|
| Files on disk | ✅ | ❌ (cloud API) | ❌ (proprietary DB) |
| Markdown | ✅ | partial | ❌ |
| Wikilinks `[[like this]]` | ✅ | partial | ❌ |
| Claude can read directly | ✅ | needs MCP server | ❌ |
| Free | ✅ | paid for teams | ✅ |

Use Obsidian. There is no second-best option.

## Install

Download from [obsidian.md](https://obsidian.md). Open it. Create a new vault — pick a path you'll remember. I use `~/Documents/Vault`. The path matters: Claude will `cd` into this directory.

## Vault structure

Use this skeleton (a copy is in [../templates/vault-skeleton/](../templates/vault-skeleton/)):

```
~/Documents/Vault/
├── CLAUDE.md              ← project instructions for Claude (your personal OS rules)
├── README.md
├── Inbox/                 ← raw captures, process daily
├── Daily Notes/           ← YYYY-MM-DD.md
├── Projects/              ← active work, one file per project
├── Areas/                 ← life domains: Health, Finance, Career, etc.
├── Goals/                 ← vision → yearly → monthly → weekly
├── People/                ← one file per person you want to track
├── Learning/              ← books, articles, ideas
├── Resources/             ← frameworks, references, SOPs
├── Archive/               ← finished/dead items (never delete)
├── Templates/             ← reusable note templates
└── _attachments/          ← images, PDFs
```

## Conventions that make Claude effective

These aren't arbitrary — Claude relies on them.

1. **Wikilinks for everything internal**: `[[Areas/Health]]`, not markdown links. Lets Claude graph-walk.
2. **Tags**: `#domain/subtopic`. Example: `#health/sleep`, `#career/snowball`.
3. **Frontmatter**: every project, person, and learning item starts with YAML frontmatter (see [../templates/](../templates/)).
4. **Daily notes**: `YYYY-MM-DD.md` in `Daily Notes/`. Always.
5. **Never delete**: move to `Archive/`. Claude reads history.
6. **Descriptive filenames**: `cold-email-campaign.md` not `untitled.md` or `note-1.md`.

## Initialize as a git repo

Highly recommended. Lets you `/push` to a private GitHub repo for backup + version history.

```bash
cd ~/Documents/Vault
git init -b main
git add .
git commit -m "initial vault"
```

If you want it backed up off-machine, create a **private** repo on GitHub and push.

## Open Claude Code inside the vault

```bash
cd ~/Documents/Vault
claude
```

Now Claude's working directory is your vault. Try:

```
Read my CLAUDE.md and list every folder. Tell me which folders look empty and propose one note each I should create this week.
```

That's the loop. Talk to Claude. It reads and writes your notes. Your second brain is alive.

## A note on Obsidian's mobile app

Obsidian on iOS / Android syncs your vault if you point it at iCloud Drive (or [Obsidian Sync](https://obsidian.md/sync) — paid). You get the same notes on your phone. Claude doesn't run on mobile, but you can capture there and let Claude process on desktop.

Next: [04-wispr-flow.md](04-wispr-flow.md).
