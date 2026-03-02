---
description: Generate a publication-quality scientific diagram or plot using PaperBanana
argument-hint: <figure description or method text>
allowed-tools: [Bash, Read]
---

# PaperBanana: Generate Figure

The user wants to generate a scientific figure. Their input: $ARGUMENTS

## Instructions

1. **Check setup** — verify PaperBanana is installed:

```bash
test -d ~/PaperBanana && echo "installed" || echo "not installed"
```

If not installed, tell the user to run `/paper-banana-setup` first.

2. **Read the skill** for full guidance — it is loaded automatically. For mode details,
   read `skills/paper-banana/references/pipeline-modes.md`. For prompt writing help,
   read `skills/paper-banana/references/prompt-guide.md`.

3. **Recommend a mode** based on the user's needs:
   - Quick draft → `vanilla`
   - Best quality → `dev_planner_critic` (default recommendation)
   - Maximum quality → `dev_full`

4. **Launch Streamlit** (recommended for interactive use):

```bash
cd ~/PaperBanana && source .venv/bin/activate && streamlit run demo.py
```

Or use CLI for batch use:

```bash
cd ~/PaperBanana && source .venv/bin/activate && python main.py \
  --task_name diagram \
  --exp_mode dev_planner_critic \
  --retrieval_setting none
```

5. **Guide the user** on pasting their input into the Streamlit UI and selecting settings.

6. **Remind** about saving output to `images/` for Quarto integration.
   Read `skills/paper-banana/references/quarto-integration.md` if they ask about embedding.
