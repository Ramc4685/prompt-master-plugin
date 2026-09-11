# prompt-master (Claude Code plugin)

A Claude Code plugin wrapper around [nidhinjs/prompt-master](https://github.com/nidhinjs/prompt-master),
a skill that writes production-ready prompts for any AI tool with zero wasted tokens.

Covers Claude, ChatGPT/Codex, Grok, Gemini, o3-class reasoning models, Qwen, Ollama,
Cursor, Windsurf, Cline, Copilot, Bolt/v0/Lovable, Devin, Perplexity, Midjourney,
DALL-E, Stable Diffusion, ComfyUI, Sora, Runway, ElevenLabs, Zapier/Make/n8n, and more.

## What is in here

```
.claude-plugin/plugin.json       plugin manifest
.claude-plugin/marketplace.json  local marketplace entry
commands/prompt.md               /prompt-master:prompt slash command
skills/prompt-master/SKILL.md    the skill (auto-activates on prompt requests)
skills/prompt-master/references/ templates.md and patterns.md
```

## Install

From this directory's parent, add it as a local marketplace and install:

```bash
claude plugin marketplace add /Users/ramc/Documents/Code/prompt-master-plugin
claude plugin install prompt-master@prompt-master-marketplace
```

## Use

The skill activates on its own when you ask for a prompt:

```
Write me a prompt for Cursor to refactor my auth module
```

Or invoke it explicitly:

```
/prompt-master:prompt fix this GPT prompt for Midjourney instead
```

## Updating from upstream

The skill and its references are copied verbatim from upstream. To refresh:

```bash
git clone --depth 1 https://github.com/nidhinjs/prompt-master.git /tmp/pm
cp /tmp/pm/SKILL.md skills/prompt-master/SKILL.md
cp /tmp/pm/references/*.md skills/prompt-master/references/
```

Bump `version` in `.claude-plugin/plugin.json` and `.claude-plugin/marketplace.json` to match.

## License

MIT. Skill content by Nidhin Joseph Nelson; see LICENSE.
