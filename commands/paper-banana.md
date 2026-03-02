---
description: Generate a publication-quality scientific diagram or plot using PaperBanana
argument-hint: <figure caption>
allowed-tools: [Bash, Read]
---

# PaperBanana: Generate Figure

The user wants to generate a scientific figure. Caption/description from arguments: $ARGUMENTS

## Instructions

1. **Check setup** — verify PaperBanana is installed:

```bash
test -d ~/PaperBanana && echo "installed" || echo "not installed"
```

If not installed, tell the user to run `/paper-banana-setup` first.

2. **Collect input** — ask the user for:
   - Their method/description text (can be pasted directly in chat)
   - A figure caption (if not already in `$ARGUMENTS`)
   - Output directory (default: `~/PaperBanana/output`)

3. **Run the CLI generator** — pipe the method text and run `generate.py`:

```bash
cd ~/PaperBanana && source .venv/bin/activate && \
echo "METHOD_TEXT_HERE" | python generate.py \
  --caption "CAPTION_HERE" \
  --output ~/figures \
  --candidates 5 \
  --mode dev_planner_critic \
  --critic-rounds 2
```

Replace `METHOD_TEXT_HERE` with the user's method text and `CAPTION_HERE` with their caption.

For longer method text, write it to a temp file first:

```bash
cat > /tmp/method.txt << 'EOF'
METHOD_TEXT_HERE
EOF
cd ~/PaperBanana && source .venv/bin/activate && \
python generate.py --caption "CAPTION_HERE" --output ~/figures < /tmp/method.txt
```

4. **Report results** — the script prints saved image paths to stdout. Tell the user
   where the images were saved and suggest opening the output directory:

```bash
open ~/figures
```

5. **Quarto integration** — if the user wants to embed in slides, read
   `skills/paper-banana/references/quarto-integration.md` for layout patterns.

## Mode quick-reference

| Mode | Use when |
|------|----------|
| `vanilla` | Quick draft |
| `dev_planner_critic` | Best quality (default) |
| `dev_full` | Maximum pipeline |
