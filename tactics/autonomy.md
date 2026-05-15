# Autonomy Tactics

Default Claude asks permission for everything. That's a useful default for code that ships to production. For a personal OS, it's friction.

The goal: let Claude **check, act, and report** instead of **ask, wait, then act**.

## 1. Put it in your global `CLAUDE.md`

The single most effective change. The template at [../templates/global-CLAUDE.md](../templates/global-CLAUDE.md) already includes this — but make it your own:

```
**Be autonomous.** Don't ask before checking. Just check, act, and report findings.
Don't ask before reading my files. Don't ask before searching the web.
Ask before: writing to files outside the vault, sending email, pushing to git, deleting anything.
```

This single block changes the default behavior across all sessions.

## 2. Pre-allow safe tools in settings

`~/.claude/settings.json`:

```json
{
  "permissions": {
    "allow": [
      "Read(*)",
      "Edit(*)",
      "Write(*)",
      "Bash(git status*)",
      "Bash(git diff*)",
      "Bash(git log*)",
      "Bash(ls*)",
      "Bash(cat*)",
      "Bash(rg*)",
      "Bash(grep*)",
      "Bash(find*)",
      "Bash(head*)",
      "Bash(tail*)",
      "WebFetch",
      "WebSearch"
    ]
  }
}
```

You can let the `fewer-permission-prompts` skill scan your recent sessions and recommend additions.

## 3. Cap, don't gate

Instead of "ask first," constrain what Claude can do without asking:

> "You can read anything in the vault. You can write anywhere in `Daily Notes/`, `Inbox/`, and `Learning/` without asking. Anything else, show me a diff first."

Now Claude is autonomous in safe zones, deliberate in risky ones.

## 4. Trust but verify

When you delegate, **verify**.

After a multi-file change:

```
show git status and a one-line summary per file
```

After a research run:

```
list every source you used, one URL per line
```

After Claude "sets things up":

```
run a quick smoke test — does X actually work end-to-end?
```

This is how you stay safe at higher autonomy.

## 5. Hard boundaries

These should always require confirmation, even with maxed-out autonomy:

- Anything irreversible (`rm`, `git push --force`, dropping tables).
- Anything external (sending email, posting on social, creating PRs, calls to paid APIs at scale).
- Anything that modifies someone else's data.

Encode these as `"ask"` entries in your permissions.

## 6. Background agents

For long-running work, you can spawn a background agent and keep working. Most useful for:

- "Process my inbox of 80 raw captures into the right folders."
- "Read all my Daily Notes from this month and produce a monthly summary."
- "Watch the deploy logs and ping me if anything errors."

`/loop` lets you set up self-pacing recurring tasks; `/schedule` lets you cron a remote agent. See `docs/06-skills.md` and the built-in `schedule` skill.

## 7. Standing orders

Add specific autonomous behaviors as standing orders in your global `CLAUDE.md`:

```
**Standing orders:**
- If I haven't checked my inbox folder in 3 days, surface it on session start.
- If a Project frontmatter says `due:` in the next 7 days, mention it at the top of my daily note.
- If I haven't journaled in 2 days, ask me one question to break the streak.
```

These run whenever they're relevant, without you asking.

## 8. Anti-patterns

- "Be fully autonomous" — too vague, Claude won't know which things to clear with you.
- Giving every tool the green light — you lose visibility into what's happening.
- Skipping verification — autonomy without verification is how things go wrong silently.

The principle: **maximum autonomy in safe zones, deliberate friction at the boundaries.**
