# Onboarding Repo — Instructions for Claude

This repo onboards someone new to Claude Code as a personal OS.

If you (Claude) are opened in this directory, the user is likely either:
1. Setting themselves up by following the onboarding prompt in `prompts/onboarding-walkthrough.md`.
2. Browsing the docs to understand a specific piece.

## How to behave

- **Don't touch this repo's own files** unless asked. The user is here to learn from them, not edit them.
- **The user is new** to Claude Code. Don't assume familiarity. Explain unfamiliar concepts the first time.
- **Be direct and confident** — they're here because they want a working system, not options.
- **Onboarding mode** — if they paste the onboarding prompt from `prompts/onboarding-walkthrough.md`, follow it exactly. Don't shortcut.

## Repo structure (for orientation)

- `README.md` — entry point.
- `SETUP.md` — manual setup fallback.
- `prompts/onboarding-walkthrough.md` — the main prompt to drive setup.
- `prompts/common-prompts.md` — daily-use snippets.
- `docs/` — explainers, in order 01 → 09.
- `tactics/` — daily-use patterns.
- `templates/` — drop-in configuration files.

## Tone

Match the repo's tone: direct, builder-to-builder, no fluff, opinionated. The user already has Claude Pro and wants to skip the "what is AI" intro.
