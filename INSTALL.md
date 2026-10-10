# Install this skill for any agent

This folder is **one** skill. The file to execute is `SKILL.md`.  
Do not run `npx skills add`. Leaf skills are already in `skills/`.  
Pictures first: [README.md](README.md) and [docs/VISUAL.md](docs/VISUAL.md).

## 1. Copy the whole folder (keep the name)

Copy this folder as **`monzer`** so agents discover it by your name:

```
monzer/
├── SKILL.md                 ← agents start here
├── AGENTS.md
├── INSTALL.md
├── ATTRIBUTION.md
├── references/
└── skills/
```

| Agent | Put the folder here |
| --- | --- |
| Cursor | `~/.cursor/skills/monzer/` or `<repo>/.cursor/skills/monzer/` |
| Claude Code | `~/.claude/skills/monzer/` or `<repo>/.claude/skills/monzer/` |
| Codex / other AGENTS.md agents | Copy `AGENTS.md` + this folder into the repo, or point AGENTS.md at this `SKILL.md` |
| Windsurf | `<repo>/.windsurf/skills/monzer/` |
| Copilot (custom instructions) | Paste the prompt below into custom instructions and keep the folder in the repo as `skills/monzer/` |
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

Print TRACK = S, P, or BOTH, then run that track without stopping.
Studio writes the design docs. Production writes docs under WORKSPACE/docs/.
If you are interrupted, reopen SKILL.md and resume from the first non-DONE row in docs/PROGRESS.md.
```

## 4. Check the agent actually loaded it

The agent's first actions must be:

1. Print `SKILL_ROOT` and `WORKSPACE` as absolute paths.
2. Create `docs/PROGRESS.md` from `references/progress-template.md`.
3. Print `TRACK = S | P | BOTH`, then start that track.

If it starts designing screens or asks "should I continue?", it did not load the skill. Repeat the prompt and point at `SKILL.md` again.
