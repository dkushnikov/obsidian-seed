# Obsidian Seed

## What this is

A wizard (single markdown file) that turns Claude Code into a personal Obsidian vault setup assistant. Discovery-first: interviews the user, derives structure from answers.

## Canonical files

- `seed.md` — the wizard itself. Version tag: `<!-- seed vYYYY.MM.DD -->`
- `PHILOSOPHY.md` — design thinking
- `CHANGELOG.md` — release history
- `README.md` — public-facing description

## Conventions

- Calendar versioning: `YYYY.MM.DD` (not semver). Tag format: `vYYYY.MM.DD`
- CHANGELOG.md updated with every release
- GitHub Releases: attach `seed.md` as asset so users can download just the file
- Issue template: `.github/ISSUE_TEMPLATE/feedback.md`

## Vault mirror

This repo has a mirror in the author's Obsidian vault (`Projects/Obsidian Wizard/`). The vault copy contains:
- `index.md` — project status, history, roadmap (private, not published)
- `messages.md` — communications and feedback log (private)
- Redirect stubs for `wizard.md`, `PHILOSOPHY.md`, `README.md` pointing back here

**This repo is canonical.** Vault copies are redirects, not sources.

## Companion project

[claude-environment](https://github.com/dkushnikov/claude-environment) — multi-machine Claude Code setup. Seed = vault content, Environment = infrastructure around it.

## When editing seed.md

- Preserve the version tag on line 1: `<!-- seed vYYYY.MM.DD -->`
- All 11 phases (0-10.5) must remain — reorder/edit content, don't drop phases
- The questionnaire (before Phase 0) is critical — it determines session scope
- Quick Start Checklist (near the end) should stay in sync with phases
- Test changes by running the wizard in an empty vault before releasing
