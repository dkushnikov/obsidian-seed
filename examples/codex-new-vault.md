# Example — New Vault in Codex

**A fictional walkthrough.** Dana is not a real person and this is not a report from a pilot. It shows what the first session and the second look like when the agent is Codex rather than Claude Code. The author's own non-interactive runs of this path are summarised in [guides/environments.md § Verified runs](../guides/environments.md#verified-runs).

---

## About Dana

Dana is a product manager at a mid-sized SaaS company. Eight years in product, two teams, a lot of decisions that live in Slack threads and in her head. She uses ChatGPT daily for drafting and has started using Codex for small scripts. She has never used Obsidian.

What she wants: a place where her product decisions, the reasoning behind them, and the open questions survive longer than a Slack thread, and an AI that knows that context when she asks for help with the next decision.

## The first session

She installs Obsidian, creates an empty vault called `Product`, and downloads `seed.md` into it. In a terminal:

```
cd ~/Obsidian/Product
git init
codex
```

Codex opens with its default permission mode, *Ask for approval*: it may edit files inside the folder and will pause before anything outside it. Dana types: *"Follow the guide in seed.md."*

### Phase 0 came first

Before any question about her life, Codex created five files and showed each one:

- `AGENTS.md` — the vault's instruction file, with the *Session start* and *Session end* procedures and a note that `CLAUDE.md` imports it.
- `CLAUDE.md` — one line, `@AGENTS.md`.
- `_claude/MEMORY.md`, `_claude/TODO.md` — empty, with headings.
- `_claude/session-logs/2026-11-12 — Setup.md` — today's log, created now, not at the end.

Then it asked the questionnaire. Dana had an hour, no notes to import, one vault, no wearable. Plan: Phase 0–3 today, goals next time.

### Discovery

The questions were the same as for anyone. Her answers were about decisions: *"I think in trade-offs. I'm good at making the call and bad at remembering why I made it."* Codex used that later: it proposed a `Decisions/` folder with a one-page decision template (context, options, call, reason, what would change my mind) alongside `Product/`, `Team/`, `Learning/` and `Outside/`.

She removed `Outside/` ("this vault is work") and kept five areas.

### Conventions and foundation

Frontmatter on every note, wiki links, a `## Related files` section. `_meta/Me.md` in twenty lines. `_meta/Areas.md` with five rows.

Each time a file was written, Codex added a line to the session log. When Dana said *"let's make the decision template the default for new decisions"*, a dated line appeared in `_claude/MEMORY.md` the same minute.

### Closing

Fifty minutes in, Dana said *"wrap up"*. Codex rewrote *Next step* in `_claude/TODO.md` (*"draft Goals/Goals 2026.md from the three open questions in Me.md"*), updated memory, finished the log, and committed with `setup: vault structure and continuity files`.

## The second session, next day

```
cd ~/Obsidian/Product
codex
```

Dana's first message: *"let's continue"*. The first line of the answer:

> vault context loaded (last log: 2026-11-12 — Setup.md)
>
> Yesterday: setup, five areas, decision template adopted. Next step: draft Goals 2026 from the three open questions in Me.md. No TODO items older than 7 days. Start there?

She said yes. Forty minutes later she had a goals file and two decisions in `Decisions/`, each with a reason she would otherwise have forgotten.

## What was different from Claude Code

- Codex read `AGENTS.md` directly. Claude Code would have read it through `CLAUDE.md`. Same file, same session procedures, no second copy.
- Codex's own memory stayed off (it is off by default). Everything that mattered went into `_claude/MEMORY.md`, which is what the second session read.
- Nothing else. The method is the same; the mechanism is one file name.

## Where Dana hit friction

- **Permission prompts at first.** Every `git commit` and anything outside the folder asked for approval, because the sandbox protects `.git`. Expected; she approved each and learnt what the boundary was.
- **The log at the start felt odd.** An empty log file before any work. By the second session she understood why: closing the window early would have lost nothing.
- **She wanted ChatGPT's memory of her.** It is a different product with a different store. Her rules for working with AI she later wrote with [Atlas Seed](https://github.com/dkushnikov/atlas-seed) and pasted into both.

## Is this example for you?

Try this path if you already have Codex, or prefer OpenAI's models, and want the agent to read and write the vault for you. If you have no terminal at all, see [Ravi's example](chatgpt-new-vault.md). If you use Claude Code, see [Sarah](non-technical.md) or [Marcus](technical.md); only the file name differs.
