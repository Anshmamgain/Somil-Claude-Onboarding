# Common Prompts

Copy-paste prompts for things you'll do every day. Tweak to taste.

## Daily

### Morning brief
```
Good morning. Run my brief:
- Read today's calendar.
- Check yesterday's daily note for anything that slipped.
- Check Inbox for any unprocessed captures.
- Tell me the ONE thing I should do first, and why.
```

### Evening reflection
```
End of day. Update today's daily note with my reflection.
Ask me 3 questions: what went well, what slipped, what I'm avoiding.
Then propose tomorrow's ONE big thing based on context.
```

### Process inbox
```
Process Inbox/. For each raw capture:
- Identify what it is (note, idea, task, person, learning).
- Move to the right folder with proper naming.
- Add frontmatter.
- Link to anything related already in the vault.
Show me a summary table of what you did before committing.
```

## Weekly

### Sunday review
```
Run my weekly review:
- Aggregate the last 7 daily notes.
- For each active Project, give me a 1-line status: on track / slipping / blocked.
- Highlight 3 wins, 3 things I avoided.
- Propose next week's ONE big thing with a reason.
- Save it as Weekly Reviews/YYYY-WW.md.
```

### Goals check
```
Read Goals/. Compare what I said I'd do this month vs. what actually happened (use Projects/ and Daily Notes/).
Tell me what's on track, what's drifting. Don't be polite about it.
```

## Research

### Brief on a topic
```
Research <TOPIC>. Use multi-source — at least 4 sources, mix of official docs, news, and 1-2 expert opinions.
Synthesize into 5 paragraphs assuming I already know <ADJACENT TOPIC>.
Cite each major claim. Save to Learning/<topic-slug>.md.
```

### Compare two options
```
Compare <A> vs <B> for <USE CASE>. Use multi-source.
Output: a table (Price, Features, Best for, Worst for, My take) and a 2-paragraph synthesis.
Pick a winner for my use case and defend it. I'll push back if you're wrong.
```

### Meeting prep
```
I have a meeting with <PERSON> from <COMPANY> at <TIME>.
- Pull their LinkedIn, recent press, and anything in my People/ folder.
- Surface what's NOT obvious from their LinkedIn.
- Suggest 3 questions worth asking.
- Save to People/<their-name>.md and link from today's daily note.
```

## Capture

### Save an idea
```
Capture: <IDEA>. Drop into Inbox/ with a descriptive filename.
Don't expand or interpret. Just save it as raw text.
```

### Save a learning
```
Save a learning item:
- Title: <>
- Source: <book/article/video/podcast>
- URL: <>
- My takeaway: <>
Use Templates/learning.md and save to Learning/.
```

### Save a meeting
```
I just had a call with <PERSON>. Here's what happened: <STREAM OF CONSCIOUSNESS>.
Update their People/ note. Pull action items into today's daily note as tasks.
```

## Decisions

### Pre-mortem a decision
```
I'm thinking about <DECISION>. Steel-man the case against it.
What would go wrong? What am I underestimating? What's the cheapest way to test before committing?
```

### Check a claim
```
Verify or refute: "<CLAIM>". Use at least 3 independent sources.
If sources disagree, tell me which one I should trust and why.
```

## Maintenance

### Vault audit
```
Audit my vault:
- Files in wrong folders.
- Daily notes with no frontmatter.
- Projects with `status: active` that haven't been updated in 30+ days.
- People with `last_contact` older than 90 days that I said I'd stay close to.
Output a checklist I can act on. Don't fix anything yet.
```

### Memory cleanup
```
Run a consolidate-memory pass. Merge duplicates, fix stale facts, prune MEMORY.md.
Show me a diff before saving.
```

### Commit and push
```
Run /push — commit everything with a sensible message and push to remote.
```

## Help

### What can you do here
```
List every skill I have installed (~/.claude/skills/) and what each one does. Suggest 2 I should be using more.
```

### What's in context
```
What's in your current context right now? List every file you've read this session and roughly how much room is left in your context window.
```
