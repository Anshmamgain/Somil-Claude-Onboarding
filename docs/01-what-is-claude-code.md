# 01 — What is Claude Code (and why it changes everything)

You already know **Claude** from claude.ai — the chat. You type, it replies. Useful, but it can't touch your files, run your code, or remember you between sessions.

**Claude Code** is the same Claude, but with a terminal, a filesystem, and tools. It lives in your shell, opens in any folder, and can:

- Read and write files on your Mac.
- Run shell commands (with your approval).
- Edit code, search across files, run tests.
- Connect to external services via MCP servers (Gmail, GitHub, your browser).
- Operate apps on your computer when given permission.
- Remember you across sessions via a memory system.

That's the difference: a chatbot answers questions; Claude Code **does work**.

---

## Why this matters for a personal OS

You don't want a chatbot you visit. You want a system that:

- Knows your schedule, goals, projects, and people.
- Writes notes for you when you talk.
- Pulls your calendar, summarizes your inbox, drafts replies.
- Tracks commitments you made and asks about them on the right day.
- Holds your context so your brain doesn't have to.

That requires read/write access to your notes, your calendar, and your files. Web chat can't do that. Claude Code can.

---

## How a Claude Code session feels

You open a terminal, `cd` into a folder, and type `claude`. A REPL starts. You talk to it. It can:

- Look at the folder it's in (the "working directory" — context).
- Read any file path you mention.
- Call tools (file editing, bash, web search, etc.).
- Hand work off to specialized **subagents**.
- Persist things to memory.

The folder you open it in matters a lot. If you open it in your **Obsidian vault**, the entire vault becomes Claude's context. That's the trick we'll use for the personal OS.

---

## The three layers you'll configure

When you finish onboarding, your Claude Code setup has three layers stacked on top of each other:

1. **Global `~/.claude/CLAUDE.md`** — loaded into every session, everywhere. Describes who you are.
2. **Project `CLAUDE.md`** — loaded only when Claude is open in that folder. Describes the project (or in our case, the vault as your personal OS).
3. **In-session memory** — short-term notes Claude writes during the conversation.

Plus the **memory system** at `~/.claude/projects/<project>/memory/` for facts Claude learns across sessions.

You don't need to memorize this. The onboarding prompt sets it all up for you.

---

## What's next

Read [02-install-claude-code.md](02-install-claude-code.md) to get it installed.
