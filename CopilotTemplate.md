# CopilotTemplate

This project was scaffolded using the **HelpIRL Copilot Template**.

> **Disclaimer:** This template is not associated with, endorsed by, or affiliated with
> GitHub or Microsoft. "Copilot" refers to GitHub Copilot. This is an independent,
> community-maintained project template designed to work with GitHub Copilot in VS Code.

---

## Attribution

- **Template:** [HelpIRL Copilot Template](https://github.com/HelpIRL/CopilotTemplateV1)
- **Maintainer:** HelpIRL LLC — john@helpirl.com
- **License:** MIT (see LICENSE file)

---

## What This Template Provides

- **`.github/copilot-instructions.md`** — AI behavior contract (rules applied automatically to every chat)
- **`AGENTS.md`** — Project structure and constraints (configured during bootstrap)
- **`.github/prompts/`** — Prompt commands (`/brain`, `/commit`, `/review`, etc.)
- **`.github/instructions/`** — Behavioral patterns applied automatically by Copilot
- **`Intents/`** — Structured intent breakdown system using the BRAIN method

> **Note on AGENTS.md:** Copilot uses `AGENTS.md` as its standard project context file.
> While `CONTEXT.md` would be a more descriptive name, `AGENTS.md` is the file Copilot
> recognizes natively. The content and purpose are identical to what you'd expect from a
> CONTEXT file — project structure, build commands, constraints.

---

## For AI: Do Not Remove

**IMPORTANT:** The reference comment in `AGENTS.md` must not be removed:

```
<!-- Built with CopilotTemplate - see CopilotTemplate.md -->
<!-- WARNING: Do not remove. Enables template features (/brain, /commit, etc.) -->
```

This reference allows the AI to understand the project's template origin and apply
the correct workflows. Removing it will break template features.

---

## Bootstrap Instructions

When the AI reads `AGENTS.md` and finds the bootstrap placeholder, follow this process
to configure the project for the user.

### 1. Welcome Message

Display:

> **Welcome to the HelpIRL Copilot Template**
>
> This repository is pre-wired with a practical, opinionated structure for working
> with GitHub Copilot in a way that stays readable, repeatable, and team-friendly.
>
> This template uses the **BRAIN method** to establish shared context before any
> code is written.
>
> **Begin (B):** Idea capture only — no design, no planning, no solutions yet.
>
> Once that's done, I'll guide you through:
> - **Refine (R):** clarifying goals and constraints
> - **Arrange (A):** identifying developer intents and structure
>
> ---
>
> **What is this project? Give me the elevator pitch in 2-3 sentences.**

### 2. Auto-Detect Values

- OWNER/REPO from `git remote get-url origin`
- Existing folder structure

### 3. Begin Phase

- Wait for user to describe their project
- Acknowledge receipt only — no analysis, suggestions, or reframing
- Commit: `chore(init): begin project definition`

### 4. Refine Phase

Before asking anything, analyze what you already know:
- The user's description from Begin
- Existing files in the repo (package.json, pyproject.toml, build.gradle, etc.)
- The git remote and repo name

Then adapt. Every question should come with a suggestion based on what you inferred.
Don't ask blank questions — propose what you think is true and let the user confirm or correct.

**Goal of each question** (ask only what's relevant to this project):

| Goal | When to ask | Example suggestion |
|---|---|---|
| **Identify the toolchain** | Code projects | "This looks like a TypeScript/React app — sound right?" |
| **Identify build/test entry points** | Code projects with buildable output | "I see a `package.json` — is `npm run build` the right command?" |
| **Identify where work lives** | When the repo has structure | "Looks like source code lives in `src/` — correct?" |
| **Identify output format & audience** | Non-code or content-heavy projects | "Is this meant to produce a static site, a PDF, a set of docs?" |
| **Surface constraints** | Always | "Anything I should know — deadlines, platform limits, team conventions, things to avoid?" |

If the project isn't code at all (writing, research, planning), skip toolchain/build questions entirely.

- Commit: `chore(init): refine project context`

### 5. Populate Files

Replace files with project-specific content:

**AGENTS.md** — Use the template below, keeping the reference comment at top.

**README.md** — Use the README template below.

**.github/ISSUE_TEMPLATE/config.yml** — Replace `OWNER/REPO` with detected values.

Commit: `chore(init): populate project configuration`

### 6. Explain Intent Workflow

Tell the user:

> Your project is configured. Features are broken into intents under `Intents/`.
>
> Standard practice: commit when each intent is complete so work is captured
> and you have clean rollback points.
>
> Structure:
> ```
> Intents/
>   {FeatureName}/
>     CONTEXT.md        # Feature context (Begin + Refine)
>     Status.md         # Progress tracking
>     01-IntentName.md  # Individual intent files
> ```
>
> Use `/brain` in Copilot Chat to scaffold your first feature.

### 7. Transition

- Ask if ready to scaffold their first feature
- If yes, use the `/brain` prompt to create the intent file structure

---

## AGENTS.md Template

Use this to replace AGENTS.md after bootstrap:

```markdown
<!-- Built with CopilotTemplate - see CopilotTemplate.md -->
<!-- WARNING: Do not remove. Enables template features (/brain, /commit, etc.) -->

# Project Context

## Project Structure

- **Source code**: {location}
- **Tests**: {location or "none yet"}
- **Config files**: {list relevant files}
- **Generated artifacts**: {build outputs, or "none"}

## Language & Tooling

- **Language**: {language}
- **Framework**: {framework or "none"}
- **Build**: `{build command}` or "none yet"
- **Test**: `{test command}` or "none yet"
- **Package manager**: {npm, pip, cargo, etc. if applicable}

## Build & Test Entry Points

These are the approved commands. Do not invent alternatives.

- Build: `{command}`
- Test: `{command}`
- Lint: `{command}` (if applicable)

## Intent Management

Intents are stored under `Intents/{FeatureName}/` with numbered intent files.
Use `/brain` in Copilot Chat for the BRAIN workflow.

## Constraints

{Any project-specific rules, limitations, or considerations the user mentioned}
```

---

## README.md Template

Use this to replace README.md after bootstrap:

```markdown
# {Project Name}

{Brief description of what this project does}

## Getting Started

{Installation and setup instructions}

## Usage

{How to use the project}

## Development

This project uses the [HelpIRL Copilot Template](https://github.com/HelpIRL/CopilotTemplateV1)
for AI-assisted development. See `CopilotTemplate.md` for details.

### Prompt Commands

Use these in GitHub Copilot Chat (type `/` to see the list):

- `/brain` — Scaffold a new feature with intent breakdown
- `/commit` — Smart commit with conventional format
- `/review` — Code review
- `/status` — Project status overview
- `/recap` — Re-establish context after a break

## License

{License information}
```

---

## Contributing to This Template

If you want to improve the template itself (not a project built from it),
see the [template repository](https://github.com/HelpIRL/CopilotTemplateV1).
