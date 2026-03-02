# PaperBanana Prompt Writing Guide

## The Core Principle

More detail = better output. PaperBanana's Planner agent converts your text into a
visual specification — the richer your input, the more accurate the diagram.

## What to Include

1. **Method steps** — numbered list of the process
2. **Component names** — exact names from your paper (encoder, projection head, etc.)
3. **Relationships** — what feeds into what (arrows, data flow)
4. **Dimensions/parameters** — embedding sizes, layer counts (optional but helpful)
5. **Figure caption** — the actual caption from your paper/slide

## Good Prompt Example

```markdown
## Method: Contrastive Learning Pipeline

1. Input pairs (positive/negative) sampled from mini-batch
2. Encoder f(·) maps inputs to embedding space (d=128)
3. Projection head g(·) applies non-linear transformation
4. NT-Xent loss computed over normalized embeddings
5. Gradients update shared encoder weights

**Figure caption:** Overview of the contrastive learning pipeline showing encoder
architecture, projection head, and loss computation.
```

## Bad Prompt Example

```
Show a machine learning diagram.
```

Too vague — no components, no relationships, no caption. Output will be generic.

## Templates

### Architecture Diagram

```markdown
## [System Name] Architecture

**Components:**
- [Component A]: [brief description]
- [Component B]: [brief description]
- [Component C]: [brief description]

**Data flow:**
1. Input enters [Component A]
2. [Component A] produces [artifact] for [Component B]
3. [Component B] outputs [result] to [Component C]
4. Final output: [description]

**Figure caption:** [Your actual figure caption]
```

### Experimental Pipeline

```markdown
## [Experiment Name] Pipeline

**Input:** [data type, format, size]
**Goal:** [what the pipeline achieves]

**Steps:**
1. [Step 1 with specific details]
2. [Step 2 with specific details]
3. [Step 3 with specific details]

**Key parameters:** [list any important hyperparameters/settings]

**Figure caption:** [Your actual figure caption]
```

### Comparison / Ablation Diagram

```markdown
## [Method A] vs [Method B] Comparison

**[Method A]:**
- [Key characteristic 1]
- [Key characteristic 2]

**[Method B]:**
- [Key characteristic 1]
- [Key characteristic 2]

**Key difference:** [what distinguishes them]

**Figure caption:** [Your actual figure caption]
```

## Tips

- Paste the actual method section from your paper — don't rewrite it
- Include variable names and notation exactly as in your paper
- Specify layout preferences if you have them ("horizontal left-to-right flow")
- For plots: include axis labels, data ranges, and what trend you want highlighted
