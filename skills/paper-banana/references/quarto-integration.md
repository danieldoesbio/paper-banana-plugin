# PaperBanana + Quarto Integration

## Saving Output

In the Streamlit UI, download the best candidate PNG. Save it to your presentation's
`images/` directory.

## Basic Embed

```markdown
## Method Overview

![](images/pipeline.png){fig-alt="Contrastive learning pipeline" width=90%}
```

## Side-by-Side Layout

```markdown
:::: {.columns}
::: {.column width="55%"}
![](images/pipeline.png){fig-alt="Pipeline diagram"}
:::
::: {.column width="45%"}
- Encoder maps inputs to embedding space
- NT-Xent loss over normalized embeddings
- Shared weights updated end-to-end
:::
::::
```

## Progressive Reveal (Fragment)

```markdown
![](images/pipeline.png){.fragment fig-alt="Pipeline diagram"}
```

Add `.fragment` to reveal on click. Combine with bullet points:

```markdown
:::: {.columns}
::: {.column width="60%"}
![](images/pipeline.png){.fragment fig-alt="Pipeline"}
:::
::: {.column width="40%"}
::: {.incremental}
- Step 1: encoder
- Step 2: projection
- Step 3: loss
:::
:::
::::
```

## High-Resolution Output for Print/Poster

Use the **Refine Image** tab in the Streamlit UI:
1. Upload your best candidate PNG
2. Request: "Upscale to 4K resolution, maintain all details"
3. Download the high-res version

For posters: 4K (3840×2160) is sufficient for A0 at 150dpi.
For papers: 2K (1920×1080) is sufficient for single-column figures.

## Styling Adjustments via Refine Tab

Upload any PNG (including your own diagrams) and request:
- "Change background to white"
- "Make the arrows thicker and darker"
- "Increase font size on all labels"
- "Use a color scheme suitable for colorblind readers"

## Recommended Workflow

1. Generate 10-20 candidates in `dev_planner_critic` mode
2. Pick best candidate from the grid
3. Use Refine tab for any style tweaks
4. Upscale if needed for print
5. Save to `images/` in your Quarto project
6. Reference in `.qmd` with `fig-alt` for accessibility

**See also:** `quarto-presentations` skill for full revealjs slide authoring.
