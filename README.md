# Somil → Claude Onboarding

> A complete, opinionated onboarding for turning Claude into your **personal operating system**.
> Designed for Claude Pro users (works fine — you'll just hit weekly limits faster than Max).

This is not "how to chat with Claude." This is the playbook for the way I (Ansh) actually use Claude every day: as a brain that holds my life, my projects, my notes, my voice, and my keyboard.

By the end you'll have:

- **Claude Code** running on your Mac as a CLI that can read/write files, run commands, and operate apps.
- An **Obsidian vault** wired to Claude so it can read and write your notes.
- **Wispr Flow** so you can talk to Claude instead of typing.
- **MCP servers** for Google (Gmail/Calendar/Drive), GitHub, and computer control.
- A **memory system** so Claude remembers you across conversations.
- A library of **skills, slash commands, and hooks** you can trigger by name.
- A **global `CLAUDE.md`** that describes who you are and how Claude should treat you.

---

## How to onboard yourself (the lazy path)

1. Install Claude Code (see [docs/02-install-claude-code.md](docs/02-install-claude-code.md) — takes 3 minutes).
2. Clone this repo somewhere sensible:
   ```bash
   cd ~/Desktop
   git clone https://github.com/Anshmamgain/Somil-Claude-Onboarding.git
   cd Somil-Claude-Onboarding
   ```
3. Open Claude Code inside the repo:
   ```bash
   claude
   ```
4. Paste the **onboarding prompt** from [prompts/onboarding-walkthrough.md](prompts/onboarding-walkthrough.md) into Claude Code.
5. Claude will then read every file in this repo, ask you a handful of questions (name, work, what apps you use, how you want it to talk to you), and set everything up — install missing tools, write your global `CLAUDE.md`, create your Obsidian vault skeleton, configure MCP servers, and pull in skills.

That's it. After ~30 minutes you have a working personal OS.

---

## How to onboard yourself (the manual path)

If you'd rather understand each piece first, read the docs in order:

| # | File | What it covers |
|---|------|----------------|
| 1 | [docs/01-what-is-claude-code.md](docs/01-what-is-claude-code.md) | Mental model: chat vs. Claude Code, what changes when Claude has a terminal |
| 2 | [docs/02-install-claude-code.md](docs/02-install-claude-code.md) | Install, login, first session |
| 3 | [docs/03-obsidian-setup.md](docs/03-obsidian-setup.md) | Vault structure, why Obsidian is Claude's brain |
| 4 | [docs/04-wispr-flow.md](docs/04-wispr-flow.md) | Voice-to-text setup; talking instead of typing |
| 5 | [docs/05-mcp-servers.md](docs/05-mcp-servers.md) | Google Workspace, GitHub, browser, computer-use |
| 6 | [docs/06-skills.md](docs/06-skills.md) | Reusable, named capabilities Claude can invoke |
| 7 | [docs/07-slash-commands.md](docs/07-slash-commands.md) | `/daily`, `/weekly`, `/review` — your custom commands |
| 8 | [docs/08-memory-system.md](docs/08-memory-system.md) | How Claude remembers you across sessions |
| 9 | [docs/09-hooks.md](docs/09-hooks.md) | Automation: things Claude does without being asked |

Then read the **tactics** folder for the actual day-to-day patterns:

- [tactics/prompting-tactics.md](tactics/prompting-tactics.md)
- [tactics/autonomy.md](tactics/autonomy.md)
- [tactics/voice-driven-workflows.md](tactics/voice-driven-workflows.md)
- [tactics/multi-source-research.md](tactics/multi-source-research.md)
- [tactics/context-management.md](tactics/context-management.md)

And use the **templates**:

- [templates/global-CLAUDE.md](templates/global-CLAUDE.md) — drop into `~/.claude/CLAUDE.md`
- [templates/project-CLAUDE.md](templates/project-CLAUDE.md) — drop into any project root
- [templates/vault-skeleton/](templates/vault-skeleton/) — Obsidian folders + a sample daily note

---

## Pro vs Max — what you actually lose on Pro

Everything in this repo works on Claude Pro. The only things you lose:

| Capability | Pro | Max |
|---|---|---|
| Claude Code usage | Yes, with weekly cap | Much higher cap |
| Long autonomous runs (multi-hour) | Tight | Loose |
| Background agents | Limited | Available |
| Model access | Sonnet + Opus (gated) | Opus default |

The strategy on Pro: use Sonnet for most things, escalate to Opus only when you actually need the heavier model. Your global `CLAUDE.md` (see template) makes this almost invisible.

---

## What this repo is NOT

- Not a generic Claude tutorial — the official docs at [docs.claude.com/claude-code](https://docs.claude.com/claude-code) cover the basics.
- Not affiliated with Anthropic.
- Not exhaustive — it's the subset that actually matters in daily use.

— Ansh (for Somil)
