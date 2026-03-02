---
description: One-time setup for PaperBanana — clones repo, installs dependencies, copies config template
allowed-tools: [Bash, Read, Edit]
---

# PaperBanana Setup

Run the one-time setup for PaperBanana.

## Instructions

**Step 1: Check if already installed**

```bash
test -d ~/PaperBanana && echo "exists" || echo "not found"
```

If already exists, skip to Step 3 (verify config).

**Step 2: Clone and install**

```bash
git clone https://github.com/dwzhu-pku/PaperBanana.git ~/PaperBanana
cd ~/PaperBanana
uv venv
source .venv/bin/activate
uv python install 3.12
uv pip install -r requirements.txt
```

**Step 3: Create config file**

```bash
test -f ~/PaperBanana/configs/model_config.yaml && echo "config exists" || \
  cp ~/PaperBanana/configs/model_config.template.yaml ~/PaperBanana/configs/model_config.yaml
```

**Step 4: Check if API key is set**

```bash
python3 -c "
import yaml, sys
with open('$HOME/PaperBanana/configs/model_config.yaml') as f:
    cfg = yaml.safe_load(f)
d = cfg.get('defaults', {})
keys = cfg.get('api_keys', {})
missing = not d.get('model_name') or not d.get('image_model_name') or not any(keys.values())
print('needs configuration' if missing else 'configured')
"
```

**Step 5: Report to user**

- If "needs configuration": Tell the user to open `~/PaperBanana/configs/model_config.yaml`
  and fill in their API key. Gemini is recommended (best concurrency for parallel generation).
  Show them the relevant section of the file using the Read tool.
- If "configured": Setup is complete. Tell them to run `/paper-banana` to generate figures.

**Note:** Never print or display the actual API key value. Only confirm presence/absence.
