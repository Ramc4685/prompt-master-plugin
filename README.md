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

Add this repo as a plugin marketplace, then install the plugin:

```bash
claude plugin marketplace add Ramc4685/prompt-master-plugin
claude plugin install prompt-master@prompt-master-marketplace
```

To work on it locally instead, point the marketplace at your clone:

```bash
claude plugin marketplace add /path/to/prompt-master-plugin
claude plugin install prompt-master@prompt-master-marketplace
```

> **Pick one, not both.** Both commands register the same marketplace name
> (`prompt-master-marketplace`). Running one after the other can leave a single
> merged entry in `~/.claude/settings.json` that carries both a `repo` and a
> `path`, which silently breaks the plugin: for a `github` source, `path` means
> *"path to marketplace.json inside the repo"*, so a local directory there points
> the manifest lookup at nothing. The plugin then still reports
> `✔ enabled` in `claude plugin list` while its skill and command never load.
> To switch between the two, remove the marketplace first:
>
> ```bash
> claude plugin marketplace remove prompt-master-marketplace
> ```
>
> A healthy GitHub-installed entry looks exactly like this — no `path` key:
>
> ```json
> "prompt-master-marketplace": {
>   "source": { "source": "github", "repo": "Ramc4685/prompt-master-plugin" }
> }
> ```

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
