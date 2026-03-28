# promptneurons

Core skills library by [Prompt Neurons, LLC](https://promptneurons.com) — available for both **Claude Code** and **Gemini/Antigravity IDE**.

## Available Skills

| Skill | Description |
|-------|-------------|
| `install-md-generator` | Generate install.md files for autonomous AI agent execution |

## Setup

### Claude Code

Add the PromptNeurons marketplace, then install:

```bash
claude plugin marketplace add https://github.com/promptneurons/promptneurons-marketplace
claude plugin install promptneurons
```

That's it — skills are now available to Claude Code.

### Gemini / Antigravity IDE

This repo ships with Gemini-ready skills in `.gemini/skills/`. Two options:

**Option A — Clone into your workspace (recommended)**

```bash
# From your project root:
git clone https://github.com/promptneurons/promptneurons.git .promptneurons

# Copy the skills into your workspace:
cp -r .promptneurons/.gemini/skills/* .gemini/skills/

# Or on Windows (PowerShell):
Copy-Item -Recurse -Force .promptneurons\.gemini\skills\* .gemini\skills\
```

**Option B — User-level install (all workspaces)**

```bash
git clone https://github.com/promptneurons/promptneurons.git ~/.promptneurons
cp -r ~/.promptneurons/.gemini/skills/* ~/.gemini/skills/

# Windows (PowerShell):
git clone https://github.com/promptneurons/promptneurons.git "$HOME\.promptneurons"
Copy-Item -Recurse -Force "$HOME\.promptneurons\.gemini\skills\*" "$HOME\.gemini\skills\"
```

**Option C — Use the pn-marketplace CLI**

```bash
npx pn-antigravity-plugin init --tier p100
npx pn-antigravity-plugin install promptneurons
```

### Verify

In Antigravity IDE, open the agent chat and ask it to generate an install.md — the skill should activate automatically.

## Repo Structure

```
.claude-plugin/          # Claude Code plugin manifest
├── plugin.json

.gemini/                 # Gemini/Antigravity-ready (just copy this)
├── plugin.json          # Antigravity-native bundle manifest
└── skills/
    └── promptneurons-skill-install-md-generator/
        └── SKILL.md

skills/                  # Source skills (Claude Code native format)
└── install-md-generator/
    └── SKILL.md
```

The `skills/` directory is the source of truth. The `.gemini/skills/` directory mirrors them with the `promptneurons-skill-` prefix that Antigravity uses for namespacing.

## Access Tiers

| Tier | Access |
|------|--------|
| **P100** (Public) | This repo — free, open source |
| **H100** (Strategic Partner) | Private repos — paid GitHub org membership |
| **H200** (Franchisee) | Private repos — paid, Antigravity IDE required |

## License

MIT — Prompt Neurons, LLC
