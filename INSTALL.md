# Install this skill for any agent

This folder is the skill. The file to execute is `SKILL.md`.  
Do not run `npx skills add`. Leaf skills are already in `skills/`.

## 1. Copy the whole folder (keep the name)

Copy `monzer-mobile-skill` so this layout stays intact:

```
mobile-app-builder/
├── SKILL.md                 ← agents start here
├── AGENTS.md
├── INSTALL.md
├── ATTRIBUTION.md
├── references/
└── skills/
```

| Agent | Put the folder here |
| --- | --- |
| Cursor | `~/.cursor/skills/mobile-app-builder/` or `<repo>/.cursor/skills/mobile-app-builder/` |
| Claude Code | `~/.claude/skills/mobile-app-builder/` or `<repo>/.claude/skills/mobile-app-builder/` |
| Codex / other AGENTS.md agents | Copy `AGENTS.md` + this folder into the repo, or point AGENTS.md at this `SKILL.md` |
| Windsurf | `<repo>/.windsurf/skills/mobile-app-builder/` |
| Copilot (custom instructions) | Paste the prompt below into custom instructions and keep the folder in the repo as `skills/mobile-app-builder/` |
| Any agent with no skill loader | Open the **app** repo as the workspace, then paste the prompt below |

Windows home = `C:\Users\<you>\`. macOS/Linux home = `~`.

## 2. Open the existing web/app repo as the workspace

The skill folder is instructions. The workspace is the product code.  
Do not run the workflow *inside* the skill folder unless that folder is also the product repo.

## 3. Paste this as the first user message

Replace the path with the real location of this folder.

```
Read this file fully and obey it as the only workflow:
<ABSOLUTE_PATH_TO_SKILL_FOLDER>/SKILL.md

SKILL_ROOT = that folder.
WORKSPACE = this repo (the existing web app / backend / any existing mobile app).

Execute phases M0 through M10 without stopping. Write docs under WORKSPACE/docs/.
If you are interrupted, reopen SKILL.md and resume from the first non-DONE row in docs/PROGRESS.md.
```

## 4. Check the agent actually loaded it

The agent's first actions must be:

1. Print `SKILL_ROOT` and `WORKSPACE` as absolute paths.
2. Create `docs/PROGRESS.md` from `references/progress-template.md`.
3. Start M0 — not app UI.

If it starts designing screens or asks "should I continue?", it did not load the skill. Repeat the prompt and point at `SKILL.md` again.
