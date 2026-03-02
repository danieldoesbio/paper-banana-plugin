---
name: paper-banana
description: Use when generating publication-quality figures, diagrams, or plots for scientific presentations or papers from a text description of methods or results
version: 1.0.0
license: Apache-2.0
---

# PaperBanana: AI Figure Generation for Scientific Presentations

Multi-agent pipeline that converts method/result descriptions into publication-quality
diagrams and plots. Pairs naturally with Quarto revealjs slides.

**License note:** Apache-2.0 for open-source research. Google has filed patents on
core workflows — avoid commercial use without legal review.

## Quick Start

If PaperBanana is not yet installed, run `/paper-banana-setup` first.

```bash
# Launch the interactive UI (recommended)
streamlit run ~/PaperBanana/demo.py
```

## Choosing a Mode

| Mode | Use when |
|------|----------|
| `vanilla` | Quick draft, low stakes |
| `dev_planner` | Need structured spec |
| `dev_planner_stylist` | Academic aesthetic matters |
| `dev_planner_critic` | Best quality (most common) |
| `dev_full` | Maximum pipeline, slowest |

**Default recommendation:** `dev_planner_critic`

Full mode details: read `references/pipeline-modes.md`

## Writing Good Input

More detail = better output. Paste the actual method section in Markdown.
Include the figure caption from your paper/slide.

Prompt templates and good/bad examples: read `references/prompt-guide.md`

## Quarto Integration

Save generated PNGs to your presentation's `images/` directory and reference normally.

Columns, fragments, upscaling guide: read `references/quarto-integration.md`

## Troubleshooting

Common issues (API key, missing dataset, model errors): read `references/troubleshooting.md`

## When to Use PaperBanana vs Alternatives

| Situation | Tool |
|-----------|------|
| Conceptual architecture / pipeline diagram | PaperBanana (`diagram`) |
| Data plot from DataFrame or CSV | PaperBanana (`plot`) or matplotlib directly |
| Simple flowchart | Mermaid in Quarto |
| Existing figure needs style tweaks | PaperBanana Refine tab |
| Photographic or microscopy figures | Not a fit — use your actual data |

**See also:** `quarto-presentations` skill for embedding figures in revealjs slides.
