# paper-banana-plugin

A Claude Code plugin for generating publication-quality scientific diagrams and plots
using [PaperBanana](https://github.com/dwzhu-pku/PaperBanana).

## Installation

```
/plugin install github:daniellusk/paper-banana-plugin
```

## Commands

| Command | Description |
|---------|-------------|
| `/paper-banana-setup` | One-time setup: clone PaperBanana, install deps, configure API key |
| `/paper-banana <description>` | Generate a scientific diagram or plot |

## Skill

The `paper-banana` skill activates automatically when you ask Claude to generate
scientific figures, diagrams, or plots for papers or presentations.

## Quick Start

1. Install the plugin (above)
2. Run `/paper-banana-setup` to install PaperBanana and configure your API key
3. Run `/paper-banana` with a description of your figure, or just ask Claude to
   generate a scientific diagram

## Requirements

- [uv](https://docs.astral.sh/uv/) package manager
- API key for Gemini (recommended), OpenAI, or Anthropic
- macOS or Linux

## License

Apache-2.0 — matches [upstream PaperBanana](https://github.com/dwzhu-pku/PaperBanana).

> **Note:** Google has filed patents on core PaperBanana workflows. Avoid commercial
> use without legal review.
