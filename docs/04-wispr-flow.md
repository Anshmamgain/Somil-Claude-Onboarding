# 04 — Wispr Flow (talk instead of type)

Typing is the bottleneck. You think faster than you type. Voice is faster than typing for ~90% of what you tell Claude.

[Wispr Flow](https://wisprflow.ai) is a Mac app that turns your voice into text **anywhere you can type** — including the Claude Code REPL. Hold a hotkey, speak, release, and your speech becomes text at the cursor.

## Install

1. Download from [wisprflow.ai](https://wisprflow.ai).
2. Open it. Grant microphone + accessibility permissions when asked.
3. Set the global shortcut. The default is **hold `Fn`**. Pick whatever you'll actually use — I keep it on `Fn`.
4. Pick a model. The default is fine. There's a higher-accuracy paid tier; the free one is good for general dictation.

## How to actually use it

Open Claude Code. Click into the REPL. Hold your hotkey. Speak the way you'd brief a smart colleague. Release.

Wispr punctuates and corrects in real time. You'll see the text appear in the REPL. Hit enter to send.

The trick is **stream of consciousness**. Don't pre-compose. Just talk.

> "Hey, I want to track all my workouts in the vault. Make a new folder under Areas called Workouts, put a README in there explaining what I'll log, and create today's note with the structure: date, type, duration, sets, energy after."

That paragraph took ~10 seconds to say. It would have taken 90 seconds to type.

## Wispr + Claude tactics

- **Long context dumps work great**. Talk for 30 seconds straight when briefing Claude on a new project. Your voice carries nuance — Claude picks it up.
- **Don't dictate code**. For code, type. Voice is for instructions, context, briefings.
- **Use it in Obsidian too**. Dictate your daily notes, your journal, your meeting recaps directly into `.md` files.
- **Keep a microphone-friendly setup**. Headset > MacBook mic. Even a $30 headset is a huge upgrade.

## Wispr quirks to know

- It capitalizes proper nouns weirdly sometimes. Tell Claude to fix obvious transcription errors in your standing instructions (your global `CLAUDE.md` template already does this).
- "Claude" sometimes transcribes as "Cloud" or "Clyde". Add a custom dictionary entry in Wispr Settings → Dictionary.
- Long pauses cut you off. Speak in continuous bursts; pause only between thoughts.

That's it. After a few days of voice-first you won't go back.

Next: [05-mcp-servers.md](05-mcp-servers.md).
