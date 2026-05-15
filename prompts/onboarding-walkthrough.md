# The Onboarding Prompt

Copy everything between the `---` lines and paste it into a fresh Claude Code session inside this repo.

Claude will then read the repo, ask you a handful of questions, and set up your personal OS end-to-end.

---

You are onboarding me to Claude Code as my **personal operating system**. I just cloned a repo by Ansh Mamgain that documents his entire setup. I want you to walk me through replicating it on my Mac, adapted to me.

**Phase 1 — Orient yourself**

1. Read every file in this repo. Start with `README.md`, then `docs/` (in order), then `tactics/`, then `templates/`, then `prompts/common-prompts.md`. You need the full picture before you ask me anything.
2. Check my system state in parallel:
   - `claude --version` (confirm Claude Code is installed)
   - `node --version && npm --version`
   - `which obsidian || ls /Applications | grep -i obsidian`
   - `ls ~/.claude/ 2>/dev/null` (existing Claude config)
   - `ls -la ~/Documents ~/Desktop 2>/dev/null | head -30` (where might his vault live?)
   - `system_profiler SPSoftwareDataType | head -10` (macOS version)
3. Summarize what's already present vs. missing — short bullet list. No fluff.

**Phase 2 — Ask me about me**

Ask me **all** of these in a single message (numbered), then wait for my reply. Do not proceed until I answer.

1. Full name + a one-liner about what you do for work.
2. The 3–5 life domains you want Claude to track (e.g., health, finance, a specific company, family, learning, a hobby).
3. Apps you live in (Gmail? Google Calendar? Notion? Linear? Slack? Specific browsers?).
4. Sleep / work schedule — when do you actually do deep work?
5. How do you want me to address you? (Name, "boss", "sir", whatever — and the tone you want: formal / casual / blunt / mentor.)
6. Existing Obsidian vault? Path? Or starting fresh?
7. What's your single biggest goal for the next 90 days?
8. Anything I should **never** do or talk about?

**Phase 3 — Install what's missing**

Based on Phase 1 + Phase 2:

- If Claude Code is missing → walk me through installing it (point to `docs/02-install-claude-code.md`).
- If Obsidian is missing → tell me to install it from obsidian.md, then create a vault at the path I gave you (or `~/Documents/Vault` by default), copying the skeleton from `templates/vault-skeleton/` and renaming files to match my name + timezone-local date.
- If Wispr Flow is missing → point me at `docs/04-wispr-flow.md`.
- Initialize the vault as a git repo if it isn't already.

**Phase 4 — Write my configuration files**

- Generate my **global `CLAUDE.md`** at `~/.claude/CLAUDE.md`. Base it on `templates/global-CLAUDE.md` but rewrite it in my voice using my Phase 2 answers. It must include: who I am, my schedule, my domains, how to address me, my prime directives, and standing orders.
- Generate a **project `CLAUDE.md`** at the root of my vault, based on `templates/project-CLAUDE.md`, that turns the vault into my personal OS.
- Create `~/.claude/projects/<vault-slug>/memory/MEMORY.md` and seed it with 2–3 entries derived from my answers (e.g., `feedback_tone.md`, `user_role.md`).
- Set up `.gitignore` in the vault so it doesn't track `.obsidian/workspace*`, `.DS_Store`, etc.

**Phase 5 — MCP servers**

Read `docs/05-mcp-servers.md`. Then:

- Ask which MCP servers I want to connect (Google Workspace, GitHub, computer-use, Obsidian CLI).
- For each I say yes to, set it up or tell me exactly what to do (e.g., paste a client ID).
- Do NOT install servers I didn't ask for.

**Phase 6 — Skills + slash commands**

- Walk me through `docs/06-skills.md` and `docs/07-slash-commands.md`.
- Propose **3 starter slash commands** based on my domains. Example: if I track health, propose `/health`. If I track a startup, propose `/biz`. Don't propose 10 — propose 3, and make sure they're things I'll actually use weekly.
- Scaffold each as a skill file in `~/.claude/skills/<name>/SKILL.md`.

**Phase 7 — Hooks (optional, ask first)**

Read `docs/09-hooks.md`. Ask me if I want any of the example hooks (auto-commit, session-end logging). Only set up the ones I confirm.

**Phase 8 — Test run**

- Open my new vault as the working directory.
- Run a fake `/daily` (or whatever my morning command is) so I can see what Claude does at the start of my day.
- Ask Claude to remember one fact about me (test the memory system — verify a file appears at `~/.claude/projects/<vault>/memory/`).
- Hand off with a short summary of what's installed, what's left, and the **3 things I should try tomorrow**.

**Rules for this whole walkthrough**

- Be direct. No "great question!" or "certainly!".
- One question at a time only inside Phase 2 (where I batched them). Elsewhere, act first and report.
- Never delete files. Never overwrite existing config without showing me a diff first.
- If something I ask for conflicts with my Phase 2 answers, push back — don't silently comply.
- After every phase, give me a one-line status: `✓ Phase N done — <one sentence>`.

Start with Phase 1 now.

---
