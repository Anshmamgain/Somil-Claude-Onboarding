# Prompting Tactics

The chat habits that work in claude.ai are not the habits that work in Claude Code. Different game, different rules.

## 1. Brief like you'd brief a colleague

Claude Code is best when you treat it like a smart, fast, slightly-too-eager colleague who just walked into the room.

**Bad:**
> "fix the bug"

**Good:**
> "There's a bug in `Areas/Health.md` — the workout log is double-counting Tuesdays because I wrote two entries by mistake. Find them, merge them, keep the higher rep count. Don't touch other days."

The good version says: what's wrong, where, why it matters, what to do, what NOT to do.

## 2. Give the goal, not the steps

If you give Claude a 10-step procedure, it executes the procedure. If you give it a goal, it can choose better steps than you'd think of.

**Steps mode:**
> "open Daily Notes/2026-05-15.md, scroll to the bottom, add a heading 'Evening Reflection', add 3 bullets..."

**Goal mode:**
> "Run my evening reflection — yesterday's note didn't have one and I want to be consistent."

Use goal mode unless you have a specific reason not to.

## 3. Have an opinion ready to be challenged

Don't ask "what should I do?" — ask "I'm thinking X because Y. Push back if that's wrong."

Claude is much better at validating/critiquing a position than at generating one from nothing. Plus you stay in the driver's seat.

## 4. Front-load context, back-load the ask

Put the situational details first, the actual ask last. This is how the model parses best.

```
I track my workouts in Areas/Health.md.
I haven't logged in 3 weeks but I worked out maybe 4 times.
I don't remember exact dates but I think Mon and Thu mostly.

→ Help me backfill plausible entries and mark them as estimated.
```

## 5. Cap output when you don't need a wall of text

> "in under 100 words"
> "one paragraph"
> "table format, 4 columns"
> "yes/no with one sentence why"

Use these constantly. Default Claude is chatty. Constrain it.

## 6. Use parallel tool calls

If Claude needs to read 4 files, you can say:

> "Read these in parallel: Projects/foo.md, Projects/bar.md, Areas/baz.md, People/qux.md. Then..."

It'll batch the reads. Way faster than serial reads.

## 7. Push back on its first answer

If Claude's first reply feels generic, just say "this feels generic — what would you really do." You'll often get the better answer second.

## 8. Don't trust summary-only updates

If Claude says "I updated 4 notes," verify. Open one of them. Read the diff. Models occasionally describe what they intended to do as if it were done.

In Claude Code, you can ask:

> "show me a git diff of every change you made in this session"

## 9. Treat each session as cheap, context as expensive

A long-running session bloats with old context. Two clean sessions are usually better than one mega-session. Use `/clear` aggressively between unrelated tasks.

## 10. When stuck, dump everything

If Claude is going in circles, paste in:
- The full file contents.
- The exact error.
- What you've already tried.
- What outcome you actually want.

90% of "Claude can't figure this out" is "I didn't give it enough context."

## 11. Name the tool you want

If you know Claude has the right capability but it's not using it:

> "use the `defuddle` skill to read this URL"
> "use the `find-docs` skill to look up Stripe's webhook API"
> "use `gh` to check PR #142 status"

Faster than letting it discover.

## 12. End with a clean handoff

When you finish a session, ask:

> "summarize what we did, what's left, and 3 things I should do tomorrow. Write it into today's daily note."

Now next session has a starting point.
