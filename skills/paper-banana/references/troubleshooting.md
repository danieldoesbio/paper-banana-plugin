# PaperBanana Troubleshooting

## Setup Issues

### "No module named X" on startup

The venv is not activated or dependencies are not installed.

```bash
cd ~/PaperBanana
source .venv/bin/activate
uv pip install -r requirements.txt
```

### "configs/model_config.yaml not found"

The config file was not created from the template.

```bash
cp configs/model_config.template.yaml configs/model_config.yaml
# Then edit model_config.yaml and add your API key
```

## API / Model Issues

### "API key not found" or authentication error

Open `~/PaperBanana/configs/model_config.yaml` and verify:

```yaml
api_keys:
  google_api_key: "your-actual-key-here"   # for Gemini
  # or
  openai_api_key: "sk-..."                 # for OpenAI
  # or
  anthropic_api_key: "sk-ant-..."          # for Claude
```

Also check that `model_name` and `image_model_name` are set under `defaults`.

### Rate limit errors during parallel generation

Reduce the candidate count. With Gemini free tier, use 5-10 candidates.
With a paid tier, 20 candidates is fine.

### Image generation returns blank or corrupted PNG

The image model API may be rate-limited or the prompt may be too long.
- Try `vanilla` mode to test the image model directly
- Shorten the input text
- Try a different image model in `model_config.yaml`

## Retrieval Issues

### "Dataset not found" with `--retrieval_setting auto`

The PaperBananaBench dataset is not installed. Use `none` instead:

```bash
python main.py --retrieval_setting none ...
```

Or install the dataset following the PaperBanana README instructions.

## Output Quality Issues

### Diagram looks generic / doesn't match my method

- Add more specific detail to the input (see `references/prompt-guide.md`)
- Use `dev_planner_critic` mode (not `vanilla`)
- Increase critic rounds to 3
- Generate more candidates (10-20) and pick best

### Text in diagram is hard to read

Use the Refine tab in the Streamlit UI:
"Increase all font sizes and make labels bold"

Or regenerate with the note: "ensure all text is legible at presentation size"
added to your input.

### Colors are not colorblind-friendly

Use the Refine tab:
"Redesign the color scheme to be accessible for deuteranopia (red-green colorblindness).
Use blue/orange instead of red/green."

## Streamlit Issues

### Port already in use

```bash
streamlit run demo.py --server.port 8502
```

### Streamlit UI is slow to load

Normal on first run — it's loading models. Subsequent loads are faster.
