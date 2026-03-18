# Obsidian Seed

Build a personal Obsidian vault that fits YOUR life — not a template. Powered by Claude Code.

## What this is

A single file that turns Claude Code into a vault setup assistant. Drop it into an empty Obsidian vault, run `claude`, and it guides you through building a personalized knowledge system from scratch.

No templates to fill in. No folder structure to copy. It asks who you are, what matters to you, and how you think — then builds a vault that reflects YOUR answers.

## Why

Every Obsidian starter vault, PARA template, and "my perfect setup" YouTube video shares the same flaw: they start with structure and ask you to fit your life into it.

This starts with you. Structure emerges from your answers, not from someone else's framework.

Read [PHILOSOPHY.md](PHILOSOPHY.md) for the thinking behind this approach.

## Quick start

### Option A: Just the seed (recommended)

1. Create an empty Obsidian vault
2. Download [`seed.md`](seed.md) into the vault root
3. Open a terminal in the vault directory
4. Run `claude` (requires [Claude Code](https://docs.anthropic.com/en/docs/claude-code))
5. Say: *"Follow the guide in seed.md"*

Claude handles everything from there — asks you questions, builds your structure, sets up conventions, creates your first notes.

### Option B: Full repo

```bash
git clone https://github.com/dkushnikov/obsidian-seed.git
cd obsidian-seed
```

This gives you:
- `seed.md` — the setup guide itself
- `PHILOSOPHY.md` — the thinking behind the approach

More content (phases, guides, examples) coming in future releases.

## What happens when you run it

1. **Questionnaire** — How much time do you have? What's your experience level? What integrations do you need? This determines which phases to run today and what to defer.

2. **Discovery** — Claude asks about your life: what you do, what matters, what you're working on, how you think. This is the most important phase — everything else builds on it.

3. **Framework** — From your answers, Claude proposes 5-10 life areas (domains). You refine until they feel right. Folders and tags are created.

4. **Conventions** — Frontmatter rules, tag system, linking habits. 30 minutes here saves hours of cleanup later.

5. **Foundation** — First notes: `Me.md` (who you are), `Areas.md` (your life map), `Goals.md` (what you're working toward).

6. **Ongoing** — Session workflow, daily reflections, people tracking, imports — added incrementally as your vault grows.

## What you get

After one session (~2 hours):
- A vault structure that matches YOUR life, not a template
- Conventions that keep things consistent as you grow
- `CLAUDE.md` tailored to your vault — so future Claude sessions know how to help
- `MEMORY.md` — Claude remembers your context between sessions
- Foundation notes: who you are, your areas, your goals
- Everything committed to git (rollback safety)

## Prerequisites

- [Obsidian](https://obsidian.md) — installed, vault created
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) — installed and working
- [Git](https://git-scm.com) — initialized in vault directory (`git init`)
- ~2 hours for the first session (you can also do 1 hour for just discovery + structure)

**Recommended:**
- [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills) — copy to `.claude/skills/` to teach Claude correct Obsidian syntax

## Philosophy

The short version:
1. **Structure follows the person** — frameworks are tools, not answers
2. **A vault is a working model, not an archive** — only keep what's alive
3. **AI is a collaborator, not a search engine** — Claude remembers, connects, challenges
4. **Conventions before content** — frontmatter and tags prevent chaos
5. **Build incrementally** — foundation first, then grow organically
6. **Git is not optional** — safety net and decision journal

The long version: [PHILOSOPHY.md](PHILOSOPHY.md)

## Status

This is an early release. The methodology behind it is battle-tested — it was developed through 40+ hours of real vault building over two weeks, and the resulting vault is in daily use. But the seed file itself hasn't been cold-tested by someone other than the author yet.

If something doesn't work as expected, Claude Code is good at adapting on the fly. Open an issue with what happened — that feedback is the fastest way to improve it.

## Related

- [Claude Environment](https://github.com/dkushnikov/claude-environment) — multi-machine Claude Code setup with data pipelines and automation. **Seed = vault content, Environment = infrastructure.** Once your vault is running, use Environment to add calendar sync, health data, cron jobs, and multi-machine support.

## Contributing

Found a bug? Got stuck somewhere? Have a suggestion?

Open an issue. Describe what happened — where you got stuck, what confused you, what you wish it had done differently. That feedback makes it better for everyone.

## License

MIT
