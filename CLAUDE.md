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

This repo has a mirror in the author's Obsidian vault (`Projects/Obsidian Seed/`). The vault copy contains:
- `index.md` — project status, history, roadmap (private, not published)
- `messages.md` — legacy single-file communications log (archived 2026-04-12)
- `communication/` — structured communications directory (replaces messages.md):
  - `releases/` — per-release comms packages (Slack drafts, outreach lists, follow-up schedules)
  - `users/` — per-user tracking files
  - `templates/` — reusable outreach message drafts
  - `feedback-log.md` — cross-user themes synthesized
- `test-personas/` — private test fixtures for cold-run validation (4 archetype personas)
- `drafts/` — pre-shipping draft content
- Redirect stubs for `wizard.md`, `PHILOSOPHY.md`, `README.md` pointing back here

**This repo is canonical.** Vault copies are redirects for public files; private vault content (index, communication, test-personas, drafts) lives only in vault.

## Companion project

[claude-environment](https://github.com/dkushnikov/claude-environment) — multi-machine Claude Code setup. Seed = vault content, Environment = infrastructure around it.

## When editing seed.md

- Preserve the version tag on line 1: `<!-- seed vYYYY.MM.DD -->`
- All 11 phases (0-10.5) must remain — reorder/edit content, don't drop phases
- The questionnaire (before Phase 0) is critical — it determines session scope
- Quick Start Checklist (near the end) should stay in sync with phases
- Test changes by running the wizard in an empty vault before releasing
