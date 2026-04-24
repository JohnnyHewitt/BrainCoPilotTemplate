---
mode: 'chat'
description: 'Template update — pull improvements from the upstream HelpIRL template'
---

# Template Update

Update this project's template files from the upstream source.

## Source Repository

```
https://github.com/HelpIRL/CopilotTemplateV1
Branch: main
```

## First: Check for Uncommitted Changes

Before proceeding, check for uncommitted changes:

```bash
git status --porcelain
```

If output is **not empty**, ask the user:

> **You have uncommitted changes.**
>
> It's easier to review or revert template updates when starting from a clean state.
>
> Would you like to commit your changes first before pulling in updates?
> 1. Yes, commit first (use `/commit`)
> 2. No, continue anyway

If user chooses to commit first, run the `/commit` prompt, then continue with the update.

## Then: Ask What to Update

Present this menu to the user:

> **What would you like to add/update?**
>
> 1. **Instructions** — AI behavior rules (copilot-instructions.md)
> 2. **Prompts** — Prompt commands (e.g., /brain, /commit)
> 3. **Skills** — Behavioral patterns (e.g., systematic-debugging)
> 4. **All** — Everything above
>
> Press Esc to cancel without making changes.

Wait for user selection before proceeding.

## What Each Selection Includes

| Selection | Files Updated |
|-----------|---------------|
| **Instructions** | `.github/copilot-instructions.md` |
| **Prompts** | `.github/prompts/*.prompt.md` |
| **Skills** | `.github/instructions/*.instructions.md` |
| **All** | All of the above |

## What is NEVER Updated

These files are **project-specific** and will NOT be modified regardless of selection:

- `README.md` — Your project documentation
- `AGENTS.md` — Your project structure and constraints
- `.github/ISSUE_TEMPLATE/` — Your issue templates
- `.github/workflows/` — Your CI/CD workflows

## Instructions

### 1. Get file lists from template repo

```bash
# Prompts
gh api repos/HelpIRL/CopilotTemplateV1/contents/.github/prompts --jq '.[].name'

# Skills/Instructions
gh api repos/HelpIRL/CopilotTemplateV1/contents/.github/instructions --jq '.[].name'
```

### 2. Fetch files using raw GitHub URLs

```
https://raw.githubusercontent.com/HelpIRL/CopilotTemplateV1/main/<path>
```

Examples:
- `https://raw.githubusercontent.com/HelpIRL/CopilotTemplateV1/main/.github/copilot-instructions.md`
- `https://raw.githubusercontent.com/HelpIRL/CopilotTemplateV1/main/.github/prompts/brain.prompt.md`

### 3. For each file in the selected categories

- Create parent directories if needed
- Fetch the latest version from template repo
- Compare with local version (if exists)
- If different or new, update the file

### 4. Important rules

- Do NOT delete local files missing from template (user may have custom files)
- Do NOT update `template-update.prompt.md` during execution (this file)

### 5. Report summary

After completion, show:
- Files updated (with change indicator)
- New files added
- Files unchanged (skipped)

Example output:
```
Template Update Complete

Updated:
  ✓ .github/copilot-instructions.md
  ✓ .github/prompts/brain.prompt.md
  + .github/instructions/systematic-debugging.instructions.md (new)

Unchanged:
  - .github/prompts/commit.prompt.md (no changes)

Run /template-update again anytime to check for updates.
```
