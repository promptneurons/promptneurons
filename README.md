# promptneurons

Core skills library by [Prompt Neurons, LLC](https://promptneurons.com) — available for both **Claude Code** and **Gemini/Antigravity IDE**.

## Available Skills

| Skill | Description |
|-------|-------------|
| `install-md-generator` | Generate install.md files for autonomous AI agent execution |
| `agent-scaffolding` | Scaffold a multi-agent workspace with AGENTS.md, .agents/, .claude/, and .gemini/ directories |

## Quick Start for Antigravity IDE

### Install Any Skill (2 commands)

```bash
git clone https://github.com/promptneurons/promptneurons.git
cp -r promptneurons/.gemini/skills/* .gemini/skills/
```

Windows (PowerShell):
```powershell
git clone https://github.com/promptneurons/promptneurons.git
Copy-Item -Recurse -Force promptneurons\.gemini\skills\* .gemini\skills\
```

That's it. Open Antigravity and the skills are available.

### Set Up a Multi-Agent Workspace

The **agent-scaffolding** skill is designed to be used _from within_ Antigravity. Once installed (via the commands above), simply ask the agent:

> "Set up this project as a multi-agent workspace"

The agent will use the `agent-scaffolding` skill to create:
- `AGENTS.md` — the bootstrap file read by all agents
- `.agents/` — the source-of-truth directory for skills, workflows, and context
- `.claude/` and `.gemini/` — platform-specific mirrors
- `CLAUDE.md` and `GEMINI.md` — copies of AGENTS.md for each platform

### Install a Specific Skill Only

```bash
# Just the install-md-generator:
mkdir -p .gemini/skills/promptneurons-skill-install-md-generator
cp -r promptneurons/skills/install-md-generator/* .gemini/skills/promptneurons-skill-install-md-generator/

# Just the agent-scaffolding:
mkdir -p .gemini/skills/promptneurons-skill-agent-scaffolding
cp -r promptneurons/skills/agent-scaffolding/* .gemini/skills/promptneurons-skill-agent-scaffolding/
```

Windows (PowerShell):
```powershell
# Just the install-md-generator:
New-Item -ItemType Directory -Force -Path .gemini\skills\promptneurons-skill-install-md-generator
Copy-Item -Recurse -Force promptneurons\skills\install-md-generator\* .gemini\skills\promptneurons-skill-install-md-generator\

# Just the agent-scaffolding:
New-Item -ItemType Directory -Force -Path .gemini\skills\promptneurons-skill-agent-scaffolding
Copy-Item -Recurse -Force promptneurons\skills\agent-scaffolding\* .gemini\skills\promptneurons-skill-agent-scaffolding\
```

## Setup for Claude Code

```bash
claude plugin marketplace add https://github.com/promptneurons/promptneurons-marketplace
claude plugin install promptneurons
```

## Other Install Methods

**User-level install** (skills available in all workspaces):

```bash
git clone https://github.com/promptneurons/promptneurons.git ~/.promptneurons
cp -r ~/.promptneurons/.gemini/skills/* ~/.gemini/skills/

# Windows:
git clone https://github.com/promptneurons/promptneurons.git "$HOME\.promptneurons"
Copy-Item -Recurse -Force "$HOME\.promptneurons\.gemini\skills\*" "$HOME\.gemini\skills\"
```

**CLI tool:**

```bash
npx pn-antigravity-plugin init --tier p100
npx pn-antigravity-plugin install promptneurons
```

## Repo Structure

```
.claude-plugin/          # Claude Code plugin manifest
├── plugin.json

.gemini/                 # Gemini/Antigravity-ready (just copy this)
├── plugin.json          # Antigravity-native bundle manifest
└── skills/
    ├── promptneurons-skill-install-md-generator/
    │   └── SKILL.md
    └── promptneurons-skill-agent-scaffolding/
        └── SKILL.md

skills/                  # Source skills (Claude Code native format)
├── install-md-generator/
│   └── SKILL.md
└── agent-scaffolding/
    └── SKILL.md
```

## Access Tiers

| Tier | Access |
|------|--------|
| **P100** (Public) | This repo — free, open source |
| **H100** (Strategic Partner) | Private repos — paid GitHub org membership |
| **H200** (Franchisee) | Private repos — paid, Antigravity IDE required |

## License

MIT — Prompt Neurons, LLC
