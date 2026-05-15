# Voice-Driven Workflows

Once Wispr Flow is set up (see [../docs/04-wispr-flow.md](../docs/04-wispr-flow.md)), the question becomes: what do you actually use voice for?

Voice wins for **briefing, capturing, and stream-of-consciousness thinking.** It loses for code, exact syntax, and precise edits.

## Patterns that work

### 1. The morning download

When you wake up, before doing anything else, open Claude Code in your vault, hit your Wispr hotkey, and talk for 30-60 seconds:

> "Okay, so it's morning, I slept badly, I have that call with X at 2, I'm anxious about the demo. The thing I really need to do today is finish Y. Yesterday I half-finished Z. Mark all that, do the daily review, and tell me what to focus on first."

That's a perfect Claude Code brief. It captures mood, schedule, anxiety, priority, history — in one breath.

### 2. The post-meeting dump

Right after a meeting, talk for 60 seconds:

> "Just got off with Priya from Acme. She's interested but worried about Z. She'll forward me to their COO next week. Action items: I send her the deck Friday, I draft a one-pager on Z, I check our pricing for their team size. Save this under People/Priya - capital P - Surname starts with K - or wherever you have her. Also add to today's daily note."

Claude updates People/Priya, your daily note, and creates the action items as tasks.

### 3. The "I had an idea while walking"

Hit Wispr, talk, save:

> "Idea — what if I tracked my reading-vs-listening ratio over months. Books I actually read vs podcasts I just consumed. Could correlate with depth of retention. Make a note in Inbox to flesh this out later."

Claude drops an idea capture into Inbox. You process it during your next `/inbox` run.

### 4. The "explain it to me" brief

When you want Claude to research something:

> "I keep hearing about <topic> and don't really get it. Give me a 5-paragraph explainer that assumes I know <related thing>, but ELI5 for the specific parts I'm missing. Use multiple sources — pull from official docs and a couple of recent articles. Save it under Learning/."

Talking the brief saves you a minute over typing it.

### 5. The journal entry

End of day, talk for 2-3 minutes:

> "End of day. Today I worked on... what went well... what I'm pissed about... what I'm grateful for... here's tomorrow's top thing..."

Save to today's daily note under an "Evening Journal" heading.

## What NOT to use voice for

- Code edits — too imprecise.
- Exact filenames, URLs, IDs — Wispr garbles them.
- Lists of more than ~5 items — they blur together.
- Anything where wording matters precisely (legal text, marketing copy you've already crafted).

For those, type.

## Wispr + Claude combo moves

### "Voice in, table out"

> "Compare X, Y, Z across price, features, support, and reliability. Use multiple sources. Output a table."

Voice the brief, get a tidy markdown table back.

### "Voice draft, Claude polish"

Dictate a messy draft of a message or post. Then:

> "Tighten this. Cut the fluff. Keep my voice. Output a clean version under the messy one."

You stay the author; Claude is the editor.

### "Voice question, Claude verifies"

Before you commit to a decision:

> "I'm thinking about doing X. Run a quick check — is there any reason that's a bad idea? Look in my notes for past mistakes, check the web for known issues, then tell me yes/no."

## Hardware

- AirPods Pro mic is fine.
- A wired headset is better.
- A standalone USB mic (e.g., Blue Yeti) is overkill but luxurious.

Whatever you use, make sure it's set as the default input in System Settings → Sound.
