# Obsidian Seed

**Turn an AI agent — Claude Code, Codex, or a plain ChatGPT chat — from a smart stranger into a thinking partner that knows who you are.**

Set up a personal Obsidian vault in one session of about an hour. The agent asks who you are, what matters, how you think, and builds a structure that fits your life. It also sets up, before anything else, the files that make the next conversation continue from this one: an instruction file, a memory, a TODO with a next step, a session journal.

Not a template. Not a chatbot integration. A method for a personal knowledge system where your AI partner has context, and where that context compounds over months.

---

## What shifts for you

**Before:** the agent is a smart stranger every session. You re-explain yourself, paste in context, get plausible-but-generic output. Your notes live in apps that don't talk to each other. Decisions made three weeks ago are gone by the time you need them.

**After:** the agent reads your values, your areas, your working style at every session start. It remembers decisions, pushes back when your reasoning drifts, surfaces patterns across weeks. Your vault is the place hard thinking happens, and your AI shows up as a partner.

The difference isn't a better model. It's the context layer you build once and that loads afterwards.

---

## Who this is for

- **Professionals with rich context in their head** that lives nowhere searchable. Coaches, consultants, therapists, engineering leaders, product managers, writers, researchers, founders.
- **People who want a thinking partner, not a note archive.** You'll use this to work through hard decisions, not to log every thought.
- **Users with one of three tools:** Claude Code or Codex in a terminal (the agent reads and writes your files), or ChatGPT in a browser (you create the files by hand from what it writes).

## Who this isn't for

- **Task managers.** Use Linear, Todoist, Things.
- **Daily journals.** Use Day One, Obsidian with a different template, or paper.
- **Team wikis.** Use Notion, Confluence. This is personal.
- **"AI that runs on its own."** The agent is reactive: it responds when you ask and does not watch in the background.
- **"Done in 15 minutes."** The first session is about an hour. Fifteen minutes gets you working rules with AI, which is a different project: [Atlas Seed](https://github.com/dkushnikov/atlas-seed).

---

## Choose your path

Two questions: new vault or existing vault, and which tool.

| | Claude Code | Codex | ChatGPT |
|---|---|---|---|
| **New vault** | `claude` in the empty vault, *"Follow the guide in seed.md"* | `codex` in the empty vault, *"Follow the guide in seed.md"* | Upload `seed.md` to a Project; the assistant writes each file as a block, you save it |
| **Existing vault** | `claude` in the vault, *"Read ADOPT.md"* | `codex --sandbox read-only` for the look, `codex` to apply | Paste the files you want reviewed; changes come as blocks |
| **Continue next time** | `claude`; the brief appears | `codex`; the brief appears | New chat in the Project; upload the current state files |
| Guide | [guides/environments.md § Claude Code](guides/environments.md#claude-code) | [§ Codex](guides/environments.md#codex) | [§ ChatGPT](guides/environments.md#chatgpt) |

### A. New vault

1. Create an empty vault in Obsidian.
2. Download [`seed.md`](seed.md) into the vault root. It is self-contained: the file templates are inside it.
3. Start your tool there and say *"Follow the guide in seed.md."* With ChatGPT, upload `seed.md` to a Project instead and say the same.

**What you have after the first session** (about an hour): a structure that reflects you; conventions; `_meta/Me.md` and `_meta/Areas.md`; and the continuity files, created in Phase 0 before discovery starts, so that closing the window early loses nothing: `AGENTS.md` (+ `CLAUDE.md`), `_claude/MEMORY.md`, `_claude/TODO.md` with a *Next step*, and today's session log. The next session reads those and shows you a brief.

**Before you start**, `seed.md` opens with *How the agent works in this system*. Five minutes. It prevents the single biggest first-time failure: expecting a proactive assistant and getting a reactive one.

### B. Existing vault

If you have a vault you've built over months or years, **don't use `seed.md`**; it assumes an empty vault. Use [`ADOPT.md`](ADOPT.md).

Adopt mode has two gears. **Look** reads your vault and reports what you have and what the method would add; it writes nothing, not even the report, which stays in the chat. **Apply** changes only the files you approved, one Git commit per change, so any one change can be undone with `git revert` while everything else stays. Running it again recognises what is already installed and does not duplicate it.

Walkthrough: [Chen's example](examples/obsidian-adopter.md) (fictional).

### C. Just want to look first

Read [PHILOSOPHY.md](PHILOSOPHY.md) for the thinking. Read the [examples](examples/) for what setup feels like. Browse [`seed.md`](seed.md) itself: the wizard is a long instruction document, nothing hidden.

---

## Prerequisites

- [Obsidian](https://obsidian.md), installed, vault created.
- One of: [Claude Code](https://code.claude.com/docs), [Codex](https://developers.openai.com/codex), or a [ChatGPT](https://chatgpt.com) account. Each product's own plan limits apply.
- [Git](https://git-scm.com), recommended for Claude Code and Codex (`git init` in the vault): the agent edits files directly and Git is the undo. Not required; without it, keep a copy before you start.
- **Time:** about an hour for the first complete session. Discovery alone fits in 30 minutes; the rest can wait for the next session because the continuity files are in place from Phase 0.

Optional: [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills) teach the agent Obsidian syntax (`.claude/skills/` for Claude Code, `.agents/skills/` for Codex).

---

## What you get

After the first session, your vault has:

- **Your structure** — folders, areas, conventions that emerged from your answers, not from a template.
- **An instruction file** — `AGENTS.md`, read by Codex directly and by Claude Code through `CLAUDE.md`; tells the agent what the vault is, where things are, what to do at the start and end of a session. In ChatGPT you paste it.
- **`_claude/MEMORY.md`** — decisions and preferences that survive between sessions. In the vault, as Markdown, so every tool sees the same record.
- **Session logs** — a journal of what each session did, created at the start of the session and read at the start of the next.
- **TODO with age markers and a next step** — `<!-- since: YYYY-MM-DD -->` on every item, and a *Next step* section the next session opens with.

These five together are the **stateful multiplier**. Each alone is modest. Together they're what makes session 10 feel different from session 1. Since November 2026 they are created in Phase 0, before discovery, and saved as you go, so an interrupted session keeps what it decided.

Plus: foundation notes (`Me.md`, `Areas.md`, `Goals.md`) drafted with the agent, and, with Git, a clean commit history.

---

## Ongoing use

Setup is the start. Two guides cover what follows:

- [**`guides/session-workflow.md`**](guides/session-workflow.md) — the session rhythm (open → work → close), saving as you go, patterns for episodic users (brain-dump before complex operations, weekly reflection, memory calibration), anti-patterns, troubleshooting.
- [**`guides/environments.md`**](guides/environments.md) — what each tool reads by itself, how to continue in a new chat, what to do when Claude Code and Codex share one vault, what to do with an install from before November 2026.

---

## Examples

Five fictional walkthroughs. They illustrate what setup and early use look like; they are not reports from a pilot.

- [**Sarah, a coach**](examples/non-technical.md) — non-technical, Claude Code, clean start. The mental-model shift ("the agent is reactive").
- [**Marcus, an engineering leader**](examples/technical.md) — technical, Claude Code, episodic use. The brain-dump pattern.
- [**Chen, an Obsidian power user**](examples/obsidian-adopter.md) — existing vault, `ADOPT.md`, per-change commits.
- [**Dana, a product manager**](examples/codex-new-vault.md) — new vault in Codex, continued the next day.
- [**Ravi, a consultant**](examples/chatgpt-new-vault.md) — no terminal: a ChatGPT Project, files created by hand.

---

## Philosophy (short version)

1. **Structure follows the person** — frameworks are tools, not answers.
2. **A vault is a working model, not an archive** — only keep what's alive.
3. **AI is a collaborator, not a search engine** — it remembers, connects, challenges.
4. **Conventions before content** — frontmatter and tags prevent chaos.
5. **Build incrementally** — foundation first, then grow.
6. **Git is the undo** — strongly recommended where an agent edits your files.

The long version: [PHILOSOPHY.md](PHILOSOPHY.md).

---

## Status

Early release. The method was developed through 40+ hours of real vault building, and the author's vault has been in daily use since. `seed.md` has been through v2026.03.29 and v2026.04.12 with feedback from external users; v2026.11.10 (this version, pending release) adds Codex and ChatGPT, moves memory into the vault and the session rules into `AGENTS.md`, and moves continuity into Phase 0.

Verified by the author on 2026-11-10 with a fictional persona, non-interactively: Claude Code 2.1.319 and Codex CLI 0.166.0 for a new vault and its continuation, including one vault shared by both tools; adopt look and re-run in Codex; adopt look, apply, re-run and revert in Claude Code. Not verified in the product: ChatGPT. Details and limits: [guides/environments.md § Verified runs](guides/environments.md#verified-runs).

If something breaks, confuses, or surprises you: open an issue. I read every one.

---

## Feedback

If you try this, tell me what happened. Success, failure, anything surprising.

- **Something broke?** Open an [issue](https://github.com/dkushnikov/obsidian-seed/issues).
- **Got stuck somewhere?** Open an issue describing where and what confused you.
- **Worked beautifully?** I'd love to hear that too.

---

## Related

- [**Atlas Seed**](https://github.com/dkushnikov/atlas-seed) — your working rules with AI in 15 minutes, and, deeper, an identity layer: who you are, separable from any vault. Same `AGENTS.md` + `CLAUDE.md` convention; the rules go into this vault unchanged. **Seed builds the vault. Atlas Seed describes the person.**
- [**Mnemon**](https://github.com/dkushnikov/mnemon) — personal library with an AI reader. Captures articles, PDFs, podcasts, YouTube, and extracts what matters *for you*. **Seed builds the vault. Mnemon fills it with knowledge.** Install after Seed when you start accumulating sources.
- [**Claude Environment**](https://github.com/dkushnikov/claude-environment) — infrastructure for a multi-machine Claude Code setup with data pipelines and automation. **Seed = vault content, Environment = infrastructure.**

---

## Contributing

Found a bug? Got stuck? Have a suggestion? Open an issue. Describe what happened: where you got stuck, what confused you, what you wish it had done differently.

---

## License

MIT
