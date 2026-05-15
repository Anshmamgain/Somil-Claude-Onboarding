# Context Management

A Claude Code session has a finite working memory (the model's context window). Big sessions slow down, get expensive, and lose accuracy. The opposite — too little context — makes Claude generic and unhelpful.

Managing context is one of the highest-leverage skills.

## The four levels of context

1. **System** — your global `CLAUDE.md`, project `CLAUDE.md`, and active memory entries. Always loaded.
2. **Working set** — files Claude has read this session. Cumulative.
3. **Conversation** — every prompt and response so far. Cumulative.
4. **Subagent results** — when Claude delegates to a subagent, only the agent's final report comes back. Saves context.

The first one is fixed. The other three you control.

## Rules

### Rule 1: Start a new session for a new task

If you finish a daily review and want to plan a project, **start a new session** (`/exit` then `claude`). Or use `/clear`. Don't pile unrelated tasks into one session.

### Rule 2: Read selectively

If a file is 2000 lines and you only need lines 100–150, ask:

> "Read `Projects/long-file.md` lines 100-150 only."

Claude has `offset` and `limit` parameters on its Read tool.

### Rule 3: Use subagents for big searches

When you don't know where something is in the vault, and finding it might mean reading 20 files, delegate:

> "Spawn an Explore subagent to find every mention of <thing> across the vault. Report back where each is, but don't paste content. I'll ask for what I need."

Now your main session sees only "found in X, Y, Z" — not the 20 file contents.

### Rule 4: Summarize and clear

When a session gets long:

> "Write a 200-word summary of what we've decided so far. Save to Daily Notes. Then I'll /clear and resume from the summary."

You preserve decisions, dump the rest.

### Rule 5: Externalize state

Anything Claude needs to remember across sessions belongs in:
- Memory files (durable facts about you).
- Project notes (state of ongoing work).
- Daily notes (what happened today).

Not in the session. Sessions are ephemeral.

## What bloats context (and how to avoid it)

| Bloat | Avoid |
|---|---|
| Pasting huge logs | Ask Claude to read the log file path directly |
| Re-reading the same file | Reference its earlier content instead of re-reading |
| Tool calls that return walls of text | Constrain output (`head -50`, `--limit 20`) |
| Long back-and-forth on a decision | Force a decision, write it down, move on |
| Repeating yourself | The model remembers — don't restate context unnecessarily |

## When the session is too long

You'll feel it: Claude getting slower, less precise, occasionally hallucinating filenames. Telltale signs:

- Claude asks for things you already gave it.
- It forgets a decision you made earlier in the same session.
- Latency creeps up.

Fix:

```
Save a session summary to today's daily note. Then exit.
```

```bash
/clear
```

Or start a new shell:

```bash
claude
```

## Context-friendly research

When researching something heavy, ask Claude to:

1. Save the synthesis to a file in the vault.
2. Report a 100-word summary back to you.

Now next session you load the file, not the entire research transcript.

## A useful command

Always available:

> "What's in your current context right now? List every file you've read this session and the rough size of our conversation."

Claude will give you a self-report. Use it as a gut-check.

## Long-running tasks

For genuinely long tasks (e.g., "process all 200 inbox notes"), use background agents:

> "Spawn a background agent to process every file in `Inbox/`. Move each to the right folder per my CLAUDE.md rules. Report when done with a per-folder count."

Your main session stays light; the agent does the heavy work in its own context.
