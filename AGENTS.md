# AGENTS

This directory is the **mobile-app-builder** skill.

1. Read `SKILL.md` in this same folder. That file is the full workflow. Follow it exactly.
2. Set `SKILL_ROOT` to this folder's absolute path.
3. Set `WORKSPACE` to the product repository (existing web app, backend, database, optional mobile app). If you are already inside the product repo, `WORKSPACE` is the repo root.
4. All leaf skills are under `skills/<name>/SKILL.md`. Do not install anything with `npx skills add`.
5. Copy `references/progress-template.md` → `<WORKSPACE>/docs/PROGRESS.md` and execute M0–M10 without stopping.
6. File shapes: `references/deliverable-templates.md`.
7. How a human installs this for Cursor / Claude / others: `INSTALL.md`.

If `SKILL.md` and any other instruction conflict, `SKILL.md` wins.
