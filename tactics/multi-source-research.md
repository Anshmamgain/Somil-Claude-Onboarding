# Multi-Source Research

Claude defaults to a single web search and a single fetch. That's fine for trivia. For anything that matters — product decisions, technical comparisons, news, biographies — you want **multiple sources in parallel** and a synthesis.

## The standing instruction

Add to your global `CLAUDE.md`:

```
**Multi-source research.** When I ask you to research anything, by default:
- Run searches across multiple engines (WebSearch, defuddle for specific URLs).
- For people, also check LinkedIn, GitHub, Twitter/X, and any provided primary sources.
- Use the find-docs skill for technical/library questions.
- Synthesize across sources; cite where each fact came from. Flag conflicts.
- Never present a single-source answer as if it were verified.
```

After that, every research task automatically goes multi-source.

## Concrete patterns

### Researching a person (e.g., a potential hire, a meeting prep)

> "Research Jane Doe — she's the COO of Acme. I want LinkedIn, recent press, any podcast appearances, anything she's said publicly about Z. Don't summarize her LinkedIn at me — tell me what's NOT on her LinkedIn that's useful."

The "tell me what's NOT obvious" framing is the unlock.

### Researching a technical comparison

> "I'm deciding between FastAPI and Litestar for a side project. Use the find-docs skill on both, plus pull recent benchmarks and 2 recent comparison posts from independent sources. Table format: performance, dev ergonomics, ecosystem maturity, who's using it. Cite each row."

### Researching a market / industry

> "Give me the state of <market> as of this month. Use 4+ sources. I want: top 3 players, recent funding events, biggest unsolved problems. Save to Learning/ as <slug>.md."

### Verifying a claim before you act on it

> "I read somewhere that <claim>. Verify or refute with at least 3 sources. If sources disagree, flag and explain why."

### Comparing two things you keep mixing up

> "What's the actual difference between X and Y? Find authoritative sources, build a side-by-side."

## Tools to know

| Tool / Skill | When to use |
|---|---|
| `WebSearch` | General web — recent news, blogs, broad questions |
| `defuddle` (skill) | Read a specific URL cleanly (better than WebFetch for articles) |
| `WebFetch` | Read a specific URL when you need raw content (e.g., a JSON endpoint) |
| `find-docs` (skill) | Official docs for any library/service/API |
| `gh` (via Bash) | GitHub orgs, repos, issues, PRs |
| Built-in MCP servers | Domain-specific (Linear, Slack, etc.) |

Tell Claude **which** tools to use when you have a preference. Otherwise it picks.

## Synthesizing across sources

The synthesis is what matters, not the source list. Push for:

- **Agreement vs disagreement** — if 3 sources agree on X but 1 disagrees, name the dissenting source.
- **Recency** — surface dates. Old sources should be flagged.
- **Authority** — official docs > company blog > random Medium post. Claude should weight accordingly.
- **What's missing** — if no one talks about Y, say so. Absence is data.

## When to escalate from Sonnet to Opus

For multi-source research with synthesis, Opus is worth it if:

- You're making a decision worth >1 day of work.
- Sources are likely to contradict.
- The topic is technical and accuracy matters.

For research → quick recap, Sonnet is fine.

> "Use Opus for this one — I'm picking a database."

Then switch back to Sonnet for follow-ups.

## Save the result

Research that isn't saved evaporates. After every research task:

> "Save the synthesis to Learning/<topic-slug>.md with proper frontmatter and a short ## Sources section at the bottom."

Now it's in your vault and Claude can use it next time.
