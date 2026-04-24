# Copilot Project Template

A starter template for AI-assisted development with strong guardrails,
repeatability, and auditability — built for GitHub Copilot in VS Code.

**This is a template repository.** Use it to scaffold new projects that work
safely and predictably with GitHub Copilot.

For attribution and license info, see [CopilotTemplate.md](CopilotTemplate.md).

---

## Table of Contents

- [Quick Start](#quick-start)
- [What You Get](#what-you-get)
- [After Setup](#after-setup)
- [Updating the Template](#updating-the-template)
- [Contributing](#contributing)
- [Files in This Template](#files-in-this-template)

---

## Quick Start

### Option 1: Use as GitHub Template

1. Click **Use this template** → **Create a new repository**
2. Clone your new repository
3. Open in VS Code with GitHub Copilot active
4. Open Copilot Chat — the bootstrap flow will guide you through setup

### Option 2: Add to Existing Project

```bash
mkdir -p .github/prompts
curl -sL https://raw.githubusercontent.com/HelpIRL/CopilotTemplateV1/main/.github/prompts/template-update.prompt.md \
  -o .github/prompts/template-update.prompt.md
```

Then use `/template-update` in Copilot Chat and choose what to install.

---

## What You Get

| Component | Purpose |
|-----------|---------|
| `.github/copilot-instructions.md` | AI behavior rules and guardrails (auto-applied) |
| `AGENTS.md` | Project structure and constraints (configured during setup) |
| `.github/prompts/` | Prompt commands (`/brain`, `/commit`, `/review`, etc.) |
| `.github/instructions/` | Behavioral patterns applied automatically by Copilot |
| `Intents/` | Structured intent breakdown system using the BRAIN method |

---

## After Setup

Once configured, your project will have:

- **AGENTS.md** — Your project structure and constraints
- **README.md** — Your project documentation (replaces this file)
- **CopilotTemplate.md** — Template attribution (keep this)

### Prompt Commands

Use these in GitHub Copilot Chat (type `/` to see the full list):

| Command | Purpose |
|---------|---------|
| `/brain "Feature"` | Scaffold a new feature with intent breakdown |
| `/commit` | Smart commit with conventional format |
| `/review` | Code review current changes |
| `/status` | Project status overview |
| `/recap` | Re-establish context after a break |
| `/test` | Run project tests |

---

## Updating the Template

To pull improvements from the template without affecting your project config:

```
/template-update
```

This updates prompt commands and instructions while preserving your `AGENTS.md`,
`README.md`, and any project-specific files.

---

## Contributing

Contributions welcome! This template is maintained by **HelpIRL LLC**.

- Issues: [GitHub Issues](https://github.com/HelpIRL/CopilotTemplateV1/issues)
- Email: john@helpirl.com

Before contributing:
1. Fork the repository
2. Create a feature branch
3. Test changes with a fresh project
4. Submit a pull request

See [CopilotTemplate.md](CopilotTemplate.md) for license and attribution.

---

## Files in This Template

```
├── AGENTS.md                          # Project context (placeholder until configured)
├── CopilotTemplate.md                 # Attribution and bootstrap logic
├── README.md                          # This file (replaced during setup)
├── LICENSE                            # MIT License
├── .github/
│   ├── copilot-instructions.md        # AI behavior contract (auto-applied)
│   ├── prompts/                       # Prompt commands (/brain, /commit, etc.)
│   └── instructions/                  # Behavioral patterns (always-on)
└── Intents/                           # Intent breakdown structure
```
