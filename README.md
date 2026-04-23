# Obsidian Seed

**Turn Claude Code from a smart stranger into a thinking partner that actually knows who you are.**

Set up a personal Obsidian vault in 1-2 hours. Claude asks you questions about who you are, what matters, how you think. It builds a vault structure that reflects your life — plus the session continuity infrastructure that makes every future Claude conversation better than the last.

Not a template. Not a chatbot integration. A methodology for building a personal knowledge system where your AI partner has context — and where that context compounds over months.

---

## What shifts for you

**Before:** Claude is a smart stranger every session. You re-explain yourself, paste in context, get plausible-but-generic output. Your notes live in apps that don't talk to each other. Decisions made three weeks ago are gone by the time you need them.

**After:** Claude reads your values, your areas, your working style at every session start. It remembers decisions, pushes back when your reasoning drifts, surfaces patterns across weeks. Your vault is the place hard thinking happens — and your AI actually shows up as a partner.

The difference isn't a better model. It's the context layer you build once, that loads forever after.

---

## Who this is for

- **Professionals with rich context in their head** that lives nowhere searchable. Coaches, consultants, therapists, engineering leaders, writers, researchers, founders. Your mental models are more refined than any of your current tools.
- **People who want a thinking partner, not a note archive.** You'll use this to work through hard decisions, not to log every thought.
- **Users comfortable with a little setup.** You'll run `claude` in a terminal, answer discovery questions for 30-60 minutes, and trust the process to build something useful.
- **Anyone already using Claude Code, or willing to.** This is a Claude Code-first methodology.

## Who this isn't for

- **Task managers.** Use Linear, Todoist, Things.
- **Daily journals.** Use Day One, Obsidian with a different template, or plain paper.
- **Team wikis.** Use Notion, Confluence. This is personal.
- **"AI that runs on its own."** Claude here is reactive — it responds when you ask, doesn't watch in the background.
- **"I want it done in 15 minutes."** First setup is 1-2 hours. The value compounds over weeks. If that tradeoff sounds bad, this is the wrong tool.

---

## Read a walkthrough before trying

Three fictional walkthroughs show what setup and early use actually look like. If any of them sounds like you, this probably works for you too.

- [**Sarah, a coach**](examples/non-technical.md) — non-technical professional, clean start. Covers the mental model shift ("Claude is reactive, not proactive") that trips up most new users.
- [**Marcus, an engineering leader**](examples/technical.md) — technical professional, episodic vault use. Shows the brain-dump protocol that makes compound interest work for users who don't open the vault daily.
- [**Chen, an Obsidian power user**](examples/obsidian-adopter.md) — existing vault with two years of refinement, using `ADOPT.md` instead of `seed.md`. Shows non-destructive adoption with per-change git commits.

---

## Quick start — three paths

### Path A: New empty vault (recommended starting point)

1. Create an empty Obsidian vault
2. Download [`seed.md`](seed.md) into the vault root
3. Open a terminal in the vault directory
4. Run `claude` (requires [Claude Code](https://docs.anthropic.com/en/docs/claude-code))
5. Say: *"Follow the guide in seed.md"*

Claude asks questions, you answer, it builds your structure. Takes 1-2 hours. At the end you have a working vault with the full session continuity infrastructure in place.

**Before you start**, `seed.md` has a section at the top called *How Claude Works in This System*. Read it. Five minutes. It explains what Claude will and won't do and prevents the single biggest first-time failure mode (expecting a proactive AI, getting a reactive one).

### Path B: You already have an Obsidian vault

If you have an existing vault you've built up over months or years, **don't use `seed.md`** — it assumes an empty vault. Use [`ADOPT.md`](ADOPT.md) instead.

`ADOPT.md` scans your existing vault, shows you what you have, proposes what seed's methodology would add, and gets your explicit approval before any change. Each change is a separate git commit — you can roll back any step. Your existing conventions, plugins, and notes stay intact.

Walkthrough: [Chen's example](examples/obsidian-adopter.md).

### Path C: Just want to see what it does first

Read [PHILOSOPHY.md](PHILOSOPHY.md) for the thinking behind this approach. Read the [examples](examples/) for concrete walkthroughs of what setup feels like. Browse [`seed.md`](seed.md) itself — the wizard is literally just a long instruction document. You can preview the whole process by reading before trying.

No cost to look. The quick start is waiting when you're ready.

---

## Prerequisites

- [Obsidian](https://obsidian.md) — installed, vault created
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) — installed and authenticated (signup is free; a [Claude](https://claude.ai) subscription covers real use)
- [Git](https://git-scm.com) — initialized in vault directory (`git init`)
- **Time:** 1-2 hours for the first session. Can also do 1 hour for just discovery and structure, return later for the rest.

**Recommended but not required:**
- [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills) — copy to `.claude/skills/` to teach Claude correct Obsidian syntax.

---

## What you get

After the first session, you have a vault with:

- **Your structure** — folders, areas, conventions emerged from your answers, not a template.
- **`CLAUDE.md`** at vault root — tells Claude how your vault works. Read at every session start.
- **`MEMORY.md`** — persistent notes Claude updates across sessions. Decisions remembered, patterns noted.
- **Session logs** — a running journal of what each session accomplished, read at the start of the next.
- **TODO with age markers** — tasks with `<!-- since: YYYY-MM-DD -->` so Claude can track drift and escalate stale items.
- **Session workflow rules** — small files that tell Claude what to do at session start (read context, show brief) and end (update TODO, memory, log, commit).

These five pieces together are the **stateful multiplier**. Each alone is modest. Together they're what makes session 10 feel qualitatively different from session 1.

Plus: foundation notes (`Me.md`, `Areas.md`, `Goals.md`) drafted with Claude's help, your first session log, and everything under git with clean commit history.

---

## Ongoing use

Setup is the start, not the end. Two guides cover ongoing use:

- [**`guides/session-workflow.md`**](guides/session-workflow.md) — the session rhythm (open → work → close), patterns for episodic users (brain-dump before complex operations, weekly reflection, memory calibration), anti-patterns, troubleshooting.
- [**`examples/`**](examples/) — the three walkthroughs for how this looks in practice over weeks.

---

## Philosophy (short version)

1. **Structure follows the person** — frameworks are tools, not answers. Your vault emerges from your life, not from PARA or Zettelkasten applied on top.
2. **A vault is a working model, not an archive** — only keep what's alive.
3. **AI is a collaborator, not a search engine** — Claude remembers, connects, challenges.
4. **Conventions before content** — frontmatter and tags prevent chaos.
5. **Build incrementally** — foundation first, then grow organically.
6. **Git is not optional** — safety net and decision journal.

The long version: [PHILOSOPHY.md](PHILOSOPHY.md).

---

## Status

This is an early release. The methodology was developed through 40+ hours of real vault building over two weeks, and the resulting vault has been in daily use for months. The seed file itself has been through v2026.03.29 and now v2026.04.12 — with feedback from several external users shaping the quality pass.

If something breaks, confuses, or surprises you: open an issue. I read every one.

---

## Feedback

If you try this, please tell me what happened. Success, failure, anything surprising.

- **Something broke?** Open an [issue](https://github.com/dkushnikov/obsidian-seed/issues).
- **Got stuck somewhere?** Open an issue describing where and what confused you.
- **Worked beautifully?** I'd love to hear that too.

Early-stage work improves with real-use feedback. Yours specifically helps more than you think.

---

## Related

- [**Mnemon**](https://github.com/dkushnikov/mnemon) — personal library with an AI reader. Captures articles, PDFs, podcasts, YouTube — extracts what matters *for you* using the `reader-context.md` that Seed creates. **Seed builds the vault. Mnemon fills it with knowledge.** Same article, different reader → different insights. Install after Seed when you start accumulating sources.
- [**Claude Environment**](https://github.com/dkushnikov/claude-environment) — infrastructure layer for multi-machine Claude Code setup with data pipelines and automation. **Seed = vault content, Environment = infrastructure.** Once your vault is running, use Environment to add calendar sync, health data, cron jobs, and multi-machine support.

---

## Contributing

Found a bug? Got stuck? Have a suggestion?

Open an issue. Describe what happened — where you got stuck, what confused you, what you wish it had done differently. That feedback makes it better for everyone.

---

## License

MIT
