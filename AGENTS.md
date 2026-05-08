# Obsidian Seed

## What this is

A wizard (single markdown file) that turns Claude Code or Codex into a personal Obsidian vault setup assistant. Discovery-first: interviews the user, derives structure from answers.

## Canonical files

- `seed.md` — the wizard itself. Version tag: `<!-- seed vYYYY.MM.DD -->`
- `PHILOSOPHY.md` — design thinking
- `CHANGELOG.md` — release history
- `README.md` — public-facing description
- `ADOPT.md` — adoption flow for existing vaults
- `guides/session-workflow.md` — ongoing use after setup

## Conventions

- Calendar versioning: `YYYY.MM.DD` (not semver). Tag format: `vYYYY.MM.DD`
- CHANGELOG.md updated with every release
- GitHub Releases: attach `seed.md` as asset so users can download just the file
- Issue template: `.github/ISSUE_TEMPLATE/feedback.md`
- Keep Claude Code and Codex support aligned: `CLAUDE.md` is Claude Code's instruction file, `AGENTS.md` is Codex's instruction file.

## Editing Guidance

- Make surgical docs changes. Do not rewrite the whole methodology unless the user asks for a hard pivot.
- Preserve the existing `_claude/` continuity workspace unless the user explicitly asks to rename it. It is historical but currently canonical.
- When adding runner-specific guidance, keep the shared Seed concepts tool-neutral and isolate tool-specific details to the instruction-surface sections.
- Do not silently replace existing user-facing claims about Claude with Codex-only wording. Prefer "agent" when the point applies to both.

## Vault Mirror

This repo has a mirror in the author's Obsidian vault (`Projects/Obsidian Seed/`). The vault copy contains private project/status material. This repo is canonical for public files.

## Companion Project

[claude-environment](https://github.com/dkushnikov/claude-environment) — multi-machine Claude Code setup. Seed = vault content, Environment = infrastructure around it. Codex support lives in Seed's vault instruction layer through `AGENTS.md`; don't make it depend on Claude-specific environment infrastructure.

## When Editing seed.md

- Preserve the version tag on line 1: `<!-- seed vYYYY.MM.DD -->`
- All 11 phases (0-10.5) must remain — reorder/edit content, don't drop phases
- The questionnaire (before Phase 0) is critical — it determines session scope
- Quick Start Checklist (near the end) should stay in sync with phases
- Test changes by running the wizard in an empty vault before releasing
