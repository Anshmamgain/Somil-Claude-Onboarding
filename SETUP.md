# Setup — Quick Reference

If you used the onboarding prompt in [prompts/onboarding-walkthrough.md](prompts/onboarding-walkthrough.md), Claude already did all of this for you. This file is the manual fallback.

## 1. Install Claude Code

```bash
# Mac (Homebrew)
brew install --cask claude-code
# or via npm
npm install -g @anthropic-ai/claude-code
```

Then:
```bash
claude
# follow the login prompt — uses your Claude Pro account
```

See [docs/02-install-claude-code.md](docs/02-install-claude-code.md) for details and troubleshooting.

## 2. Install Obsidian

Download from [obsidian.md](https://obsidian.md) and create a vault at `~/Documents/Vault` (or wherever you want — just remember the path).

Copy the skeleton:
```bash
cp -R templates/vault-skeleton/ ~/Documents/Vault/
cd ~/Documents/Vault && git init -b main
```

See [docs/03-obsidian-setup.md](docs/03-obsidian-setup.md).

## 3. Install Wispr Flow

Download from [wisprflow.ai](https://wisprflow.ai). Pair it with a global shortcut (default: hold `Fn`). After this, you can dictate into Claude Code instead of typing.

See [docs/04-wispr-flow.md](docs/04-wispr-flow.md).

## 4. Place your global `CLAUDE.md`

```bash
mkdir -p ~/.claude
cp templates/global-CLAUDE.md ~/.claude/CLAUDE.md
# then edit it — replace all <PLACEHOLDER> blocks with your details
```

## 5. Place your project `CLAUDE.md` in your vault

```bash
cp templates/project-CLAUDE.md ~/Documents/Vault/CLAUDE.md
# edit similarly
```

## 6. Connect MCP servers (optional, in order of usefulness)

```bash
# Google Workspace (Gmail/Calendar/Drive)
claude mcp add google-workspace # see docs/05 for the full command

# GitHub
claude mcp add github

# Obsidian CLI
claude mcp add obsidian-cli
```

See [docs/05-mcp-servers.md](docs/05-mcp-servers.md).

## 7. Open Claude Code inside your vault

```bash
cd ~/Documents/Vault
claude
```

Claude is now your personal OS.

## 8. Test it

Type:

```
Read my CLAUDE.md and tell me what you understand about me. Then suggest 3 things I should track in the vault this week.
```

If that works — you're done. Read the [tactics/](tactics/) folder next for daily-use patterns.
