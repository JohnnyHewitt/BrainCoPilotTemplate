# CoPilot Adaptation

> Owner: TBD  ·  Created: 2026-04-24

## Begin (raw)
<!-- 3-minute brain dump. Do not edit or reinterpret. -->

Make this template and the BRAIN method work with GitHub CoPilot. The CLAUDE.md file will need to be changed. The .claude folder structure is also incorrect for CoPilot. Use the BRAIN method to facilitate these changes.

## Refine (scope)
- **Goal**: Adapt the HelpIRL template and BRAIN method to work with GitHub CoPilot in VS Code, replacing Claude Code-specific structure with CoPilot equivalents.
- **In scope**:
  - Replace `CLAUDE.md` → `.github/copilot-instructions.md`
  - Replace `.claude/commands/` → `.github/prompts/` (prompt files)
  - Replace `.claude/skills/` → `.github/instructions/` (instructions files)
  - Remove/replace `.claude/hooks/` and `.claude/settings.json`
  - Update `CONTEXT.md` (bootstrap placeholder) to reference CoPilot workflow
  - Update `ClaudeTemplate.md` → equivalent bootstrap doc for CoPilot
  - Update `README.md` to reflect CoPilot usage
  - Scrub Claude-specific language from BRAIN method and all commands
- **Out of scope**:
  - Dual Claude+CoPilot support (CoPilot-only target)
  - CoDex adaptation (separate future effort)
  - `.claude/hooks/` replacement (no CoPilot equivalent; omit for now)
- **Definition of Done**:
  - A fresh clone of the repo, opened in VS Code with CoPilot, works end-to-end: custom instructions load automatically, `/brain` and other prompts are invocable, bootstrap flow guides a new user through project setup
- **Constraints**:
  - Preserve BRAIN method logic and phase rules intact
  - Keep MIT attribution
  - `.github/` folder is acceptable as location (works locally, not GitHub-only)
  - BRAIN method language should be AI-agnostic (no "Claude", "ChatGPT", etc.)
- **Risks**:
  - CoPilot prompt files have no programmatic side effects (can't run git commands) — BRAIN/commit flows become guidance-only, not automated
- **Resources**:
  - VS Code CoPilot custom instructions docs
  - VS Code prompt files docs
- **Dependencies**: None
