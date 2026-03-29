# Changelog

## 2026.03.29

### Session Lifecycle
- Expanded: Phase 9 renamed "Session Lifecycle" — onboarding, offboarding, deferral escalation
- Added: Session onboarding concept (read context → show brief → contextual suggestions)
- Added: TODO `<!-- since: YYYY-MM-DD -->` markers + 3-tier deferral escalation (7d / 14d / 21d)
- Added: Protocol + Skill pattern for repeatable operations
- Added: Session offboarding checklist (TODO, memory, log, commit)
- Changed: Session logs moved from `Goals/Session Logs/` to `_claude/session-logs/`

### Environment
- Added: Phase 0.6 "Understand the environment model" — layered config (Person → Domain → Project), when to add infra
- Expanded: claude-environment reference from one-liner to structured explanation

### Vision
- Added: "What's Next" section with two future directions:
  - Knowledge Store — companion vault for external sources, AI-assisted extraction
  - Work Context — thesis on why company AI fails without personal context layer (Personal AI)

### Adopting v2 in an existing vault

If you set up your vault with an earlier version of the seed, ask Claude to run this migration. Copy the block below into your conversation:

```
Read the updated seed.md (focus on Phase 0.6, Phase 9, and "What's Next").
Then check my vault against these changes and apply what's missing:

1. Session onboarding: if .claude/rules/session-onboarding.md doesn't exist,
   create a minimal one that reads CLAUDE.md, MEMORY.md, last session log,
   and _claude/TODO.md at session start, then shows a brief.

2. TODO markers: check _claude/TODO.md — if any items are missing
   <!-- since: YYYY-MM-DD --> markers, add them (use today's date
   for items with unknown age).

3. Session logs location: if session logs live in Goals/Session Logs/,
   move them to _claude/session-logs/ and update any references
   in CLAUDE.md.

4. Session offboarding: if .claude/rules/session-offboarding.md doesn't
   exist, create a minimal one: update TODO, update memory, finalize
   session log, git commit.

5. CLAUDE.md: add a "Session Lifecycle" section if missing — reference
   the onboarding and offboarding rules.

Show me what you plan to change before applying.
```

Phase 0.6 (environment model) and "What's Next" (Knowledge Store, Work Context) are awareness — read them, no vault changes needed.

### Minor
- Added: Lessons Learned #15 (session lifecycle as multiplier) and #16 (TODO markers prevent drift)
- Updated: Quick Start Checklist — added session onboarding rule setup
- Updated: Folder structure — `_claude/session-logs/` added

## 2026.03.18
- Added: cross-reference to [claude-environment](https://github.com/dkushnikov/claude-environment) in README
- Added: version tag in seed.md (`<!-- seed v2026.03.18 -->`)
- Added: CHANGELOG.md
- Added: GitHub issue template for feedback
- Added: CLAUDE.md with project conventions
- Changed: Quick Start checklist — front-loaded session continuity (TODO.md, session-logs, MEMORY.md)
- Added: walk-up chain documentation in Phase 0.3
- Added: skills limitation warning in Phase 0.1

## 2026.03.11
- Fixed: 10 personal data leakage items deidentified
- Fixed: 4 assumption/bias items removed
- Improved: multi-vault section generalized

## 2026.03.09
- Initial public release
- 11 phases (0-10.5): discovery, framework, conventions, goals, people, imports, session workflow
- Questionnaire for adaptive session planning
- Quick start checklist
- Plugin recommendations
