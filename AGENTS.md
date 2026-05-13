# Obsidian Seed — Codex Compatibility

This repository is Claude Code-first. `CLAUDE.md` is the canonical project instruction file and Seed's methodology should remain framed around Claude Code unless the maintainer explicitly decides otherwise.

When working in Codex:

- Read and follow `CLAUDE.md` as the source of truth for repository conventions.
- Treat `.claude/rules/` as the canonical session lifecycle rules. If Codex cannot load those files automatically, read and apply them manually when relevant.
- Keep `_claude/` as Seed's existing Claude workspace. Do not rename it or reframe it as a tool-neutral continuity layer in this repo without an explicit design decision.
- Preserve Claude Code wording in user-facing docs unless a change is specifically about Codex compatibility.
- Keep Codex-specific guidance small and isolated to this file or clearly marked compatibility notes.
