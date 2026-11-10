# Obsidian Seed — repository instructions for agents

Instructions for an agent working **on this repository** (the seed's own development). A user's vault gets its own instruction file from `seed.md` § Phase 0; this file is not that template.

## What this is

A method, published as a single markdown wizard (`seed.md`) plus an adoption flow (`ADOPT.md`), that turns an AI agent — Claude Code, Codex, or a ChatGPT chat — into a personal Obsidian vault setup assistant. Discovery-first: interviews the user, derives structure from answers. Continuity-first: the files that let the next session continue are created before discovery.

## Canonical files

- `seed.md` — the wizard. Self-contained: the vault file templates are embedded in Phase 0. Version tag on line 1: `<!-- seed vYYYY.MM.DD -->`
- `ADOPT.md` — the existing-vault path (look = zero writes; apply = per-item commits; undo = `git revert`)
- `guides/environments.md` — what Claude Code, Codex and ChatGPT read by themselves, how to continue in each, shared use, pre-November-2026 installs
- `guides/session-workflow.md` — ongoing use after setup
- `examples/` — fictional walkthroughs, labelled as such; not pilot results
- `PHILOSOPHY.md` — design thinking
- `CHANGELOG.md` — release history
- `README.md` — public-facing description

## Conventions

- One method, one process. Environment-specific mechanism lives in `guides/environments.md`; `seed.md` and `ADOPT.md` say "the agent" and point there. Do not fork the wizard per environment.
- The vault instruction file is `AGENTS.md` with `CLAUDE.md` = `@AGENTS.md`. The vault state is `_claude/MEMORY.md`, `_claude/TODO.md`, `_claude/session-logs/`. The `_claude/` name is historical and stays.
- `seed.md` is self-contained: a template that a user's vault needs is embedded in `seed.md`, not kept in a separate folder the user would have to download.
- Calendar versioning: `YYYY.MM.DD` (not semver). Tag format: `vYYYY.MM.DD`.
- `CHANGELOG.md` updated with every release.
- GitHub Releases: attach `seed.md` as an asset so users can download just the file.
- Issue template: `.github/ISSUE_TEMPLATE/feedback.md`.

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

## Companion projects

- [atlas-seed](https://github.com/dkushnikov/atlas-seed) — working rules with AI in 15 minutes, and the identity layer. Same `AGENTS.md` + `CLAUDE.md` convention.
- [claude-environment](https://github.com/dkushnikov/claude-environment) — multi-machine Claude Code setup. Seed = vault content, Environment = infrastructure around it.

## When editing seed.md

- Preserve the version tag on line 1: `<!-- seed vYYYY.MM.DD -->`
- All 11 phases (0-10.5) must remain — reorder/edit content, don't drop phases. Phase 0 is continuity-first: it creates the instruction file and the `_claude/` state before discovery.
- The questionnaire (before Phase 0) is critical — it determines session scope
- Quick Start Checklist (near the end) should stay in sync with phases
- The embedded templates in Phase 0 are the single source; `ADOPT.md` and `guides/environments.md` point to them, never copy them
- Test changes by running the wizard in an empty vault before releasing, in at least one agent that writes files (Claude Code or Codex); label anything not run in a product as unverified
