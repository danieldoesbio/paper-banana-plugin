# PaperBanana Pipeline Modes

## Mode Overview

PaperBanana has seven operational modes, each adding agents to the pipeline.

| Mode | Agents Active | Speed | Quality | Use When |
|------|--------------|-------|---------|----------|
| `vanilla` | Visualizer only | Fastest | Low | Rough draft, exploring ideas |
| `dev_planner` | Planner → Visualizer | Fast | Medium | Need structured visual spec |
| `dev_planner_stylist` | + Stylist | Medium | Medium-High | Academic aesthetic matters |
| `dev_planner_critic` | + Critic (iterative) | Slow | High | Best quality, most common choice |
| `dev_full` | All agents | Slowest | Highest | Maximum pipeline |
| `demo_planner_critic` | Demo variant | Slow | High | Interactive demo |
| `demo_full` | Demo variant | Slowest | Highest | Interactive demo, full |

## Agent Descriptions

**Retriever** — Finds reference diagrams from the PaperBananaBench dataset to guide
generation style. Only active when `--retrieval_setting auto` and dataset is installed.

**Planner** — Converts scientific text into a detailed visual specification. This is
the most important agent — a good plan leads to a good diagram.

**Stylist** — Refines the visual spec to meet academic aesthetic standards (clean lines,
consistent color schemes, professional typography).

**Visualizer** — Generates candidate images from the text specification. Can run up to
20 candidates in parallel. Pick the best from the output grid.

**Critic** — Reviews generated images and provides improvement feedback. The
Visualizer then regenerates based on feedback. Runs 2-3 rounds by default.

## Retrieval Settings

| Setting | Behavior |
|---------|----------|
| `auto` | Automatically finds relevant reference diagrams (requires dataset) |
| `manual` | You specify reference diagram IDs |
| `random` | Random references (for ablation study) |
| `none` | No references — use this if dataset not installed |

## CLI Usage

```bash
cd ~/PaperBanana
source .venv/bin/activate

python main.py \
  --task_name diagram \
  --exp_mode dev_planner_critic \
  --retrieval_setting none
```

For plots (data visualizations):

```bash
python main.py \
  --task_name plot \
  --exp_mode dev_planner_critic \
  --retrieval_setting none
```

## Candidate Count Recommendations

- Quick iteration: 5 candidates
- Normal use: 10 candidates
- Thorough search: 20 candidates (parallel, same cost)

## Critic Rounds

- 1 round: minimal refinement
- 2-3 rounds: best quality/speed tradeoff (recommended)
- 4+ rounds: diminishing returns
