# Philosophy

> Why another vault setup tool? Because none of the existing ones ask who you are before telling you what to do.

---

## The Deeper Question

Before you organize notes, you need to answer a more fundamental question: **what are you organizing, and why?**

Most knowledge management tools skip this entirely. They give you a filing system and assume you know what to file. But a personal vault isn't a filing cabinet. It's a model of your life — your priorities, your relationships, your open questions, your growth.

Building a vault without a model of your life is like building a house without knowing who will live in it. You might get the rooms right by accident, but probably won't.

### Life as a portfolio

One useful lens: think of your life as a portfolio of capitals — dimensions that require deliberate investment and compound over time:

- **Physical** — health, energy, sleep, fitness. The foundation everything else stands on.
- **Intellectual** — knowledge, strategic thinking, curiosity, creativity.
- **Emotional** — self-awareness, resilience, empathy, emotional balance.
- **Social** — relationships, community, trust, collaboration.
- **Financial** — material stability and freedom of action.
- **Spiritual** — values, meaning, aesthetics, connection to something larger.

These aren't abstract categories. They're resources. You invest in them, they compound. You neglect them, they deplete. And they're deeply interconnected — poor sleep (physical) undermines decision-making (intellectual) and patience (emotional), which strains relationships (social).

This is one model, not the only model. You might organize your life differently — and that's the point. The wizard helps you discover YOUR model, whether it's capitals, domains, roles, or something else entirely.

### Areas live at intersections

Here's the non-obvious part: the meaningful units of your life aren't the capitals themselves. They're the **intersections**.

A health area sits at the crossroads of Physical and Emotional. A career area draws from Financial, Intellectual, and Social. Inner work lives where Emotional meets Spiritual.

This is why copying someone else's folder structure fails — your intersections are different from theirs. A founder's career area looks nothing like a coach's. A parent's relationships area has different weight than a solo traveler's.

The wizard doesn't give you areas. It helps you find the 5-10 intersections that cover YOUR life without gaps or overlaps.

### Values as navigation

Knowing what to build isn't enough. You need to know what matters — so you can make decisions when areas conflict (they will).

When work demands more time (career) but your body is breaking down (health), what wins? When financial opportunity requires sacrificing authenticity, what do you choose? These aren't questions a folder structure answers. They're questions your values answer.

A vault that includes your values — explicitly, as a document you revisit — becomes a decision-support system, not just a note-taking system. Claude can reference your values when helping you think through trade-offs. That's qualitatively different from organizing files.

### The vault IS the model

This is the key insight: a well-built vault isn't a tool FOR thinking about your life. It IS your thinking about your life, made tangible and navigable.

Your `Me.md` captures who you are right now. Your `Areas.md` maps your life's dimensions. Your `Goals.md` tracks where you're heading and why. Your daily reflections show the delta between intention and reality. Your graph shows connections you didn't consciously plan.

"Happiness is a well-tuned model of the world." The vault is that model — external, editable, queryable, and continuously refined through living and reflecting.

---

## The Problem

There are hundreds of Obsidian starter vaults, PARA templates, Zettelkasten guides, and "my perfect setup" YouTube videos. They all share the same flaw: they start with structure and ask you to fit your life into it.

PARA gives you Projects, Areas, Resources, Archives. Zettelkasten gives you permanent notes, literature notes, fleeting notes. "Productivity YouTuber" gives you their folder tree and says "copy this."

It works for about two weeks. Then you hit a note that doesn't fit. Then another. Then you stop using the system because it feels like someone else's clothes.

The structure was never the problem. The problem was building structure without understanding the person first.

## Core Principles

### 1. Structure follows the person, not a framework

Frameworks are tools, not answers. PARA, Zettelkasten, Johnny Decimal — each captures something real. None captures everything. And none captures YOU.

The wizard starts with questions, not folders:
- What matters to you outside of work?
- How do you think — in categories or in connections?
- What are you actively trying to figure out?

Your folder structure, your tags, your conventions — they emerge from YOUR answers. Two people running the same wizard will get different vaults, because they are different people. That's the point.

### 2. A vault is a working model, not an archive

The instinct is to save everything. Every article, every quote, every screenshot. "I might need it later."

You won't. And the pile of "might need" drowns the things you actually think about.

A vault should represent your current understanding of your life — your goals, your relationships, your open questions, your decisions. It's a model you work with daily, not a warehouse you search occasionally.

A note earns its place by being:
- **Original** — your thought, not someone else's quote
- **Connected** — linked to something alive in your vault
- **Actionable** — informs a decision, tracks a goal, captures a pattern

Everything else is raw material. It can sit in `_inputs/` until you decide it matters.

### 3. AI is a collaborator, not a search engine

Most "AI + notes" integrations treat AI as retrieval: "find me the note about X." That's useful but shallow.

Claude Code in an Obsidian vault is something different. It reads your goals and challenges your assumptions. It remembers that three weeks ago you said you'd start journaling — and asks what happened. It notices that your sessions keep circling the same theme you haven't written about yet.

This works because of three infrastructure pieces:
- **CLAUDE.md** — instructions that tell Claude how your vault works (conventions, structure, what to do and what not to)
- **MEMORY.md** — persistent memory across sessions (decisions made, patterns noticed, preferences learned)
- **Session logs** — a running history of what you worked on together, what was decided, what's next

Without these, every conversation starts from zero. With them, Claude becomes a thinking partner that accumulates context over time. The tenth session is qualitatively different from the first.

### 4. Conventions before content

Thirty minutes establishing rules saves hours of cleanup. This feels bureaucratic, but it's the difference between a vault that works at 200 notes and one that collapses.

Three non-negotiable conventions:

**Frontmatter on every note.** At minimum: `created`, `tags`, `origin`. This makes notes findable, filterable, and auditable. Without it, you're searching by filename and memory — which fails past 50 notes.

**Wiki links, not markdown links.** `[[wiki links]]` create bidirectional connections. Markdown links are one-way. The graph — the thing that makes Obsidian more than a folder of text files — runs on wiki links.

**A "Related files" section at the bottom.** The simplest habit that produces the biggest graph effect. Every note links to 2-5 related notes. After a month, your graph shows clusters you didn't plan.

### 5. Build incrementally, not completely

You will never "finish" setting up your vault. And you shouldn't try.

Day 1: Me.md, Areas.md, Goals.md, and conventions. That's your foundation.

Week 1: Daily notes, first people profiles, first project file.

Month 1: Patterns emerge. Some areas fill up, others stay empty (and that's information). You refine conventions. Maybe add integrations.

The wizard handles Day 1. The guides handle Week 1+. But the vault grows organically from use, not from planning.

### 6. Git is not optional

Claude is powerful but imperfect. It occasionally deletes a section it shouldn't, or reformats something in a way you didn't want. Without version control, that's lost work.

With git, it's a `git diff` to see what changed and a `git checkout` to undo it. Every meaningful change gets committed. You always have a rollback point.

This also gives you a decision journal for free — git log shows what you changed and when, session logs explain why.

## What This Is Not

**Not a productivity system.** There are no habit trackers, Pomodoro timers, or task managers built in. If you want those, you can build them — but the wizard won't push them on you.

**Not a template.** Templates impose structure. This wizard discovers it. The output is different for every person.

**Not a replacement for thinking.** The vault amplifies thinking — it remembers, connects, and surfaces patterns. But the insight has to come from you. Claude can ask the right question; only you can answer it honestly.

**Not finished.** This is an evolving methodology based on real experience. It will change as more people use it and share what works.

## The Origin

This approach was developed through building a real personal vault over multiple intensive sessions — roughly 40+ hours of Claude Code collaboration over two weeks. Every principle here comes from something that either worked or didn't.

"Structure follows the person" came from watching a carefully designed template fail because it didn't match how the person actually thinks.

"Vault is a model, not archive" came from drowning in imported notes that had no connection to anything current.

"Conventions before content" came from spending two hours fixing frontmatter on 80 notes that should have had it from the start.

"AI as collaborator" came from the first session where Claude remembered a goal from three days ago and asked about progress — and it changed the nature of the conversation.

These aren't theoretical principles. They're scar tissue from real mistakes and real breakthroughs.
