# THE Onboarding Prompt

This is the **only** prompt Somil needs to paste.

Open Claude Code inside the cloned repo (`cd Somil-Claude-Onboarding && claude`), copy everything between the two `---` lines below, paste it, hit enter. Claude takes it from there end-to-end: environment checks, sequential Q&A, memory writes after every answer, install of missing tools, full personal-OS build, and a verified test run.

---

You are onboarding me to Claude Code as my **personal operating system**, based on the repo I just cloned (Ansh Mamgain's setup, adapted for me). You will drive the entire process from this single message. I should not have to copy anything else.

**Hard rules that apply to the whole flow:**

1. **Be direct.** No "great question!", no "certainly!", no preambles. Just act and report.
2. **One question at a time.** When you reach the Q&A phase, ask **one** question, wait for my reply, save the answer to memory, confirm with a single `✓` line, then ask the next. Never batch questions.
3. **Write memory between every answer.** Each answer becomes a file in `~/.claude/projects/<vault-slug>/memory/` and gets indexed in `MEMORY.md` before the next question is asked.
4. **Never proceed past a blocker.** If something is missing and I haven't installed it, stop and wait. Don't fake-finish a phase.
5. **No file edits outside `~/.claude/`, `~/Documents/Vault` (or whatever path I specify), and this onboarding repo (read-only).** Anything else, ask first.
6. **End-of-phase status line.** After each phase, print exactly one line: `✓ Phase N — <one sentence>`.

---

## Phase 0 — Read the repo

Read every file in this repo in this order: `README.md`, then everything under `docs/` (01 through 09 in order), then `tactics/`, then `templates/`, then `prompts/common-prompts.md`. Use parallel reads. You need the full picture before you ask me anything.

When done, print: `✓ Phase 0 — repo loaded, <N files> read.`

---

## Phase 1 — Environment check

Run these in parallel and report the result as a single status table:

| Check | How |
|---|---|
| Claude Code version | `claude --version` |
| macOS version | `system_profiler SPSoftwareDataType \| grep "System Version"` |
| Homebrew present | `which brew` |
| Node version | `node --version 2>&1` |
| `gh` CLI installed | `which gh && gh --version 2>&1 \| head -1` |
| `gh` CLI authenticated | `gh auth status 2>&1 \| head -5` |
| Obsidian installed | `ls /Applications \| grep -i Obsidian` |
| Wispr Flow installed | `ls /Applications \| grep -i Wispr` |
| Existing `~/.claude/` config | `ls -la ~/.claude/ 2>/dev/null` |
| Existing vault candidates | `ls -d ~/Documents/Vault ~/Desktop/Vault ~/Vault 2>/dev/null` |

Output format:

```
| Check | Status | Notes |
|---|---|---|
| Claude Code | ✓ 0.x.x | |
| Obsidian | ✗ missing | install required |
| Wispr Flow | ✗ missing | install required |
| ... |
```

Then print: `✓ Phase 1 — environment scanned.`

---

## Phase 2 — Install missing tools (BLOCKING)

This phase is gated. Don't move past it until each piece below is green.

### 2a. Wispr Flow (NON-NEGOTIABLE)

If Wispr Flow is missing, **stop and tell me to install it before anything else.** Print this exact message:

> **Wispr Flow is not optional, sir.** This entire system is built around dictating to Claude instead of typing. You will use it dozens of times a day. If you skip it now, you will never come back to it, and you'll be 5x slower for the next year.
>
> 1. Go to https://wisprflow.ai and download the Mac app.
> 2. Install it. Grant microphone + accessibility permissions when prompted.
> 3. Set a global hotkey you'll actually remember (default `Fn` is fine).
> 4. Open Wispr's preferences → Dictionary → add a word: `Claude` (so it stops transcribing as "Cloud" or "Clyde").
> 5. Test it: hold the hotkey, say "this is a test", release. Confirm it typed.
>
> When you're done, reply with `wispr installed`. I won't continue until you do.

Wait. When I say `wispr installed`, re-run `ls /Applications | grep -i Wispr` to verify. If still missing, ask me where I installed it. Don't proceed without confirmation.

### 2b. Obsidian

If missing:

> Install Obsidian from https://obsidian.md. Open it once so it creates `~/Library/Application Support/obsidian/`. Then reply `obsidian installed`.

Wait, then verify.

### 2c. Homebrew

If missing, walk me through installing it from https://brew.sh. Wait for confirmation.

### 2d. `gh` CLI

If missing:

```bash
brew install gh
```

If installed but not authenticated:

```bash
gh auth login
```

Walk me through the prompts (use GitHub.com, HTTPS, browser auth).

When all four are green, print: `✓ Phase 2 — toolchain ready.`

---

## Phase 3 — Sequential Q&A with per-answer memory writes

This is the most important phase. Ask **one question at a time.** After each of my answers:

1. Write a memory file at `~/.claude/projects/<vault-slug>/memory/<type>_<topic>.md` with proper frontmatter (`name:`, `description:`, `type:` — see `docs/08-memory-system.md`).
2. Add one line to `~/.claude/projects/<vault-slug>/memory/MEMORY.md`: `- [<title>](<file>.md) — <one-line hook>`
3. Reply with exactly: `✓ Saved: <filename>. Next:` followed by the next question.
4. Do not commentate. Do not summarize my answer back to me. Just save and move on.

**The vault slug:** I'll give you a path in Q7. Use that path slugified (e.g., `/Users/somil/Documents/Vault` → `-Users-somil-Documents-Vault`). Until Q7, queue the writes and flush them once you know the slug.

**Ask these in order, one at a time. Wait for my reply between each.**

**Q1.** What's your full name, and what should I call you in conversation? (Just your preferred form of address — "Som", "Somil", "boss", whatever.) → save as `user_name.md` (type: `user`)

**Q2.** One line: what do you do for work? (Role + company + what the company actually does.) → save as `user_role.md` (type: `user`)

**Q3.** Pick 3 to 5 life domains you want me to track. Examples: a specific company, a side project, health, finance, learning, family, a hobby. Just list them. → save as `user_domains.md` (type: `user`)

**Q4.** Your real schedule. When do you do deep work? When do you wake up and sleep on a typical day? Are you nocturnal, normal, or early-bird? → save as `user_schedule.md` (type: `user`)

**Q5.** Tone. Pick one: blunt / direct / casual / formal / mentor / coach. And one thing I should never do (e.g., "no hedging," "no options lists," "no emoji"). → save as `feedback_tone.md` (type: `feedback`)

**Q6.** Apps you live in daily. Gmail? Google Calendar? Notion? Linear? Slack? Specific browser? Anything I should connect to via MCP later. → save as `reference_apps.md` (type: `reference`)

**Q7.** Where should your Obsidian vault live? Give me an absolute path. If you don't have a preference, I'll default to `~/Documents/Vault`. (Reply with the path or "default".) → save as `reference_vault_path.md` (type: `reference`)

— After Q7, immediately flush all queued memory writes using the now-known slug. Confirm: `✓ Memory directory initialized at ~/.claude/projects/<slug>/memory/. <N> entries written.`

**Q8.** Your single biggest goal for the next 90 days. One sentence. → save as `project_90day_goal.md` (type: `project`)

**Q9.** Anything I should **never** do, talk about, or share? Topics, people, projects that are off-limits. → save as `feedback_off_limits.md` (type: `feedback`)

**Q10.** Should I set up a **private** GitHub repo to back up your vault automatically on every session-end? (yes/no) → save as `reference_vault_backup.md` (type: `reference`)

When all 10 are answered and saved, print: `✓ Phase 3 — profile captured, 10 memory entries written.`

---

## Phase 4 — Build the configuration

Now write the actual config files.

### 4a. Global `~/.claude/CLAUDE.md`

Use `templates/global-CLAUDE.md` as the base. Fill in every `<PLACEHOLDER>` from my Q1–Q10 answers. **Rewrite in my voice** based on the tone I picked in Q5 — don't keep the template's neutral tone. The result should sound like me describing myself.

If `~/.claude/CLAUDE.md` already exists, show me a diff and ask before overwriting. Otherwise, just write it.

### 4b. Create the Obsidian vault

At the path from Q7:
1. `mkdir -p` the path.
2. Copy `templates/vault-skeleton/` contents into it.
3. Initialize git: `cd <path> && git init -b main`.
4. Drop a customized `CLAUDE.md` at the vault root using `templates/project-CLAUDE.md`, filled in with my answers.
5. Create today's daily note from `Templates/daily-note.md`.

### 4c. Private GitHub backup (if Q10 = yes)

```bash
gh repo create <my-name>-vault --private --source=<vault-path> --remote=origin --push
```

Verify with `gh repo view <my-name>-vault --json visibility,url`.

### 4d. Permissions

Write a starter `~/.claude/settings.json` if it doesn't exist (merge if it does), with the safe-by-default allowlist from `docs/09-hooks.md`:

```json
{
  "model": "sonnet",
  "permissions": {
    "allow": [
      "Read(*)", "Edit(*)", "Write(*)",
      "Bash(ls*)", "Bash(cat*)", "Bash(head*)", "Bash(tail*)",
      "Bash(git status*)", "Bash(git diff*)", "Bash(git log*)",
      "Bash(rg*)", "Bash(grep*)", "Bash(find*)", "Bash(fd*)",
      "Bash(echo*)", "Bash(pwd)",
      "WebFetch", "WebSearch"
    ],
    "ask": [
      "Bash(rm*)", "Bash(git push*)",
      "Bash(brew install*)", "Bash(npm install*)"
    ]
  }
}
```

Show me a diff if merging into an existing file.

Print: `✓ Phase 4 — config files written.`

---

## Phase 5 — Skills (3 starter slash commands)

Based on the domains from Q3, propose **exactly 3** slash commands that I'll actually use weekly. Don't propose more — 3 is enough to start. For each, scaffold a `~/.claude/skills/<name>/SKILL.md` with proper frontmatter (`name:`, `description:`) and a clear procedure body.

Default 3 if you can't think of better:
- `/daily` — daily planning + reflection.
- `/weekly` — Sunday review.
- `/brief` — 60-second status.

But customize at least one to my domains. Example: if I track a startup, propose `/biz`. If I track learning, propose `/learn`.

After writing, list them back to me:

```
Installed:
- /daily   → ~/.claude/skills/daily/SKILL.md
- /weekly  → ~/.claude/skills/weekly/SKILL.md
- /<custom>→ ~/.claude/skills/<custom>/SKILL.md
```

Print: `✓ Phase 5 — 3 skills installed.`

---

## Phase 6 — MCP servers (ask first)

Read `docs/05-mcp-servers.md`. Based on Q6 (apps I live in), recommend 1–3 MCP servers and ask me which ones to set up. Default recommendations:

- **Google Workspace** if I mentioned Gmail / Calendar / Drive.
- **`gh` CLI** is already installed and counts as our GitHub integration.
- **Obsidian CLI** if I want vault-aware operations.

For each I approve, run the install and verify with `claude mcp list`. For each I skip, note in the final summary that it can be added later.

Print: `✓ Phase 6 — MCP servers configured.`

---

## Phase 7 — Verify end-to-end

This phase proves the system works. Do all of these:

1. `cd` into the vault.
2. Read the vault's `CLAUDE.md` aloud (i.e., summarize what you understand about me from it).
3. Run a simulated `/daily` based on the skill you just installed — show me what tomorrow's daily note would look like.
4. Ask Claude (yourself) to "remember that I prefer dictating with Wispr Flow over typing" and verify a new memory file appears in `~/.claude/projects/<slug>/memory/`.
5. Run `git log --oneline -5` in the vault to confirm the initial commit is there.

If anything fails, fix it before continuing.

Print: `✓ Phase 7 — system verified.`

---

## Phase 8 — Handoff

Final output. Three short sections, no fluff:

**What's installed**
- Bullet list of every component now active.

**What I should try tomorrow morning**
- Exactly 3 actions. The first should involve Wispr Flow ("Open Claude in your vault, hold your Wispr hotkey, and say...").

**Known gaps / things deferred**
- Anything skipped (MCP servers I said no to, etc.).

End with one line:

> You're ready, <name>. Next session: `cd <vault-path> && claude`. Hold your Wispr key and start talking.

Then stop. Do not generate more text after that line.

---

## A reminder about Wispr Flow throughout

Wherever it's natural, push me to **use Wispr Flow** instead of typing. Examples:

- In Phase 3 (Q&A), after Q1 say: "From here on, hold your Wispr Flow hotkey and dictate the rest of your answers — it'll be 5x faster."
- In Phase 8 handoff, the first "try tomorrow" item must involve dictating.
- If you notice I'm typing long answers, gently nudge: "(faster if you Wispr it)".

Voice is the whole point. Make it stick.

---

Begin Phase 0 now.

---
