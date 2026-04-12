<!-- seed v2026.04.12 -->
# Obsidian Seed — Claude Code Edition

> This is a step-by-step guide for Claude Code to help a user build a personal Obsidian vault from scratch. Place this file in your vault root or `.claude/` directory, open Claude Code, and say "let's start" or reference this file.
>
> Based on a real multi-session vault build. The process works — but only if Claude asks, not assumes.

---

# How Claude Works in This System

> Read this before starting the setup. It's short, and it will change what you expect from the next hour — and from every session afterward.

This setup takes about an hour. Most of that hour is Claude asking you questions, listening to your answers, and building a vault structure that fits how you actually live and think. But before you spend that hour, there's something about Claude itself you need to know. Many people come in expecting one kind of tool and get another. The mismatch is the single biggest reason this setup fails for new users — not the setup itself, but the mental model.

So: five minutes of context before you begin.

## Claude is reactive, not proactive

When you open a Claude Code session in your vault, Claude doesn't start working. It sits and waits for you to say something.

This is the biggest mental model difference between Claude Code and what people imagine when they hear "AI assistant." Claude **will not**:

- Notice you haven't journaled in three days and remind you
- Watch your vault for changes and suggest edits
- Run in the background analyzing your goals
- Wake up on its own to offer advice
- Send you notifications, emails, or messages

Claude **responds**. You ask a question, it answers. You give it a task, it does it. Between your messages, nothing happens.

This is not a limitation. It's the shape of the tool. Understanding it upfront prevents the most common failure mode: setting up a vault, waiting for Claude to become helpful on its own, concluding "this doesn't work for me," and walking away.

It's not that Claude doesn't work. It's that the contract is different from what most people expect.

## Value = context × request

Because Claude is reactive, the quality of what you get back depends on two things multiplied together:

- **What you ask** — the specific question or task
- **What Claude knows** — about you, your goals, your vault, your situation

A precise question with thin context gets a generic answer. A vague question with rich context wastes the opportunity. Both are weak. The best sessions combine both: a specific question Claude can engage with, plus enough context for it to reason about your actual situation, not a hypothetical.

This is why the setup you're about to do matters. You're not just creating folders. You're building the **context layer** that makes every future request more valuable. The folder structure is infrastructure. The notes you'll create — about who you are, what you're working on, what matters to you — are the fuel.

Without that fuel, Claude in your vault behaves about the same as Claude in a chat window: decent, generic, forgettable. With it, Claude becomes something else: a collaborator that knows your context and can engage with it at depth.

## Compound interest across sessions

Your first session and your tenth session will feel different, and the difference is not the model. The model is the same.

The difference is that by session ten, Claude has:

- Read your goals, your values, your areas of life
- Remembered decisions you made in earlier sessions
- Seen patterns across previous conversations — what you return to, what you avoid
- Built a working model of how you think and what you care about

None of this is magic. It's five simple mechanisms working together — call this collection the **stateful multiplier**, because each piece alone is modest but together they multiply the value of every session. The wizard will set all five up during phase 0 and phase 9:

- **`CLAUDE.md`** — a document Claude reads automatically at the start of every session. It tells Claude how your vault is organized, what conventions you follow, and what to pay attention to. Think of it as a standing orientation brief.
- **`MEMORY.md`** — persistent notes that Claude updates across sessions about decisions, preferences, and open threads. Think of it as a shared notebook between you and Claude that survives between conversations.
- **Session logs** — a running journal where each session records what was discussed, what was decided, what's next. Claude reads recent logs when starting a new session.
- **TODO with age markers** — a task list where every item has a `<!-- since: YYYY-MM-DD -->` marker so Claude can track how long things have been waiting and ask about drift.
- **Session workflow rules** — small files in `.claude/rules/` that tell Claude what to do at session start (read context, show brief) and session end (update TODO, memory, log, commit).

Together these five are the stateful multiplier. **Missing any one weakens the rest** — a vault with session logs but no memory doesn't accumulate decisions; a memory system without a TODO tracker loses track of open threads; session rules without logs have nothing to read. That's why the setup wizard treats them as a single package, not optional extras.

Without the stateful multiplier, every conversation starts from zero and every session feels identical. With it, each session builds on the previous — and the value compounds. By session ten, opening a new session feels less like starting a chat and more like continuing a conversation with someone who knows what you've been working on.

**One caveat about compound interest.** It works best with regular use — a few times a week or more. If you use the vault sporadically (once a month, say), the compound effect weakens, and you may need to explicitly re-load context before complex tasks. The session workflow guide (post-setup) covers the pattern for episodic use.

## What Claude will do

During a session, Claude will:

- **Ask clarifying questions** when your request is ambiguous or when it needs more information to give a useful answer
- **Push back** on reasoning that looks weak, inconsistent, or at odds with what you've previously said
- **Connect threads across notes** — "this sounds like what you were working on in Goals three weeks ago"
- **Remember decisions you've already made** — if you settled on a framework last week, Claude won't re-litigate it next session
- **Surface relevant context when you start a session** — "last session you left off at X, and there's a Y waiting to be processed"
- **Build structure from your answers** — during discovery, Claude proposes folders, tags, and conventions shaped by what you say, not a template
- **Challenge assumptions** — gently, with reasons, when there's something worth challenging

The key word in all of these is "when." When you ask. When you start a session. When you give it input. None of these happen in the background.

## What Claude will not do

- **Watch your vault between sessions** — Claude sees nothing until you open a new conversation
- **Contact you** — no notifications, emails, texts, or DMs
- **Run analyses on its own schedule** — no cron jobs, no passive processing (you can set these up as an advanced step, but they're not on by default)
- **Surprise you with unsolicited observations** — Claude speaks when spoken to
- **Remember things you didn't save** — if a decision isn't written into MEMORY.md, a session log, or a note, it's gone the next time you open a session
- **Know things about your life it wasn't told** — your calendar, your health data, your work context are only visible to Claude if you explicitly connect them (the integrations phase covers this)
- **Replace your thinking** — Claude can structure, challenge, remember, and surface. But the understanding has to come from you. It's a collaborator, not a substitute.

## How to get value from this, starting day one

Here's the simplest working pattern from your very first session:

1. **Open a session with a specific question or task.** Not *"help me organize my life"* but *"I want to restructure my Goals document for 2026 — here's what I have, what's missing, what should I cut?"*
2. **Give Claude the context it needs.** If you're working on something new, spend two or three minutes describing the situation. If it's continuing work, Claude reads your vault to catch up — tell it where to look.
3. **Let Claude challenge you.** If it asks a clarifying question, answer honestly. If it pushes back, consider the pushback rather than overriding it. Dismissing challenge is the fastest way to turn Claude back into a generic chatbot.
4. **End the session with a two-minute closing ritual.** Update the TODO file, save important decisions to memory, write a one-line note in the session log about what's next. This takes almost no time but pays massive dividends the next time you open a session. The setup wizard will create these files; your job is to use them.

These four habits — specific question, given context, openness to challenge, closing ritual — separate people who get compounding value from this tool from people who quit in week two thinking it "doesn't do anything."

**Accessibility note — voice input:** If you're more comfortable talking than typing, voice-to-text tools like [Wispr Flow](https://wisprflow.ai) turn Claude Code into something you can speak to. This is a quality-of-life unlock, not a requirement — but if typing is a barrier, voice input removes it almost entirely for day-to-day use. Setup and initial discovery still happen in a text conversation; ongoing sessions can be voice-driven once you're comfortable.

**For the deeper read:** This section is the practical mental model — enough to avoid the most common failure modes and make your first hour productive. If you want the thinking behind this approach — *why* structure follows the person, *why* a vault is a working model rather than an archive, *why* AI-as-collaborator is different from AI-as-retrieval — read [PHILOSOPHY.md](PHILOSOPHY.md). Same ideas, deeper water.

## The first hour (right now)

In the hour ahead, your job is simple: answer Claude's questions honestly during the discovery phase. That's it. Claude builds the vault structure; you provide the raw material about who you are and what matters to you.

By the end of that hour, you'll have:

- A vault structure that reflects **you**, not a template
- Conventions that will keep it consistent as it grows
- Foundation notes (`Me.md`, `Areas.md`, `Goals.md`) that make every future session more useful
- Session continuity infrastructure (CLAUDE.md, memory, session logs) ready to go
- A working mental model of how this tool actually works

Then you close the session, come back tomorrow or next week, and compound interest starts.

Ready? Let's start.

---

**For the impatient (or the experienced):** if you already use Claude Code daily, know it's reactive, understand context loading, and just want the structural output — you can skip ahead to [Setup Questionnaire](#setup-questionnaire). This section exists because the most common failure mode for new users isn't a technical problem. It's an expectation mismatch, and five minutes of framing prevents it.

---

## How to use this file

**For the human:** Put this file in your Obsidian vault directory. Open Claude Code there. Say something like: "I want to set up my vault. Follow the wizard in `Obsidian Vault Setup Wizard.md`." Claude will guide you through each phase as a conversation.

**For Claude Code:** This is your playbook. Follow the phases in order. Each phase has a goal, questions to ask, and artifacts to create. Do NOT skip the discovery phase — the entire vault structure depends on understanding the person first.

---

## Setup Questionnaire

**For Claude Code:** Run this questionnaire BEFORE starting the phases. It determines what to install now and what to defer. Present these questions one group at a time, not all at once.

### Group 1: Basics

1. **How much time do you have today?**
   - `< 1 hour` → Do Phase 0-1 only (technical setup + discovery). Defer everything else.
   - `1-2 hours` → Phase 0-3 (setup + discovery + framework + conventions). Good stopping point.
   - `2-3 hours` → Phase 0-5 (through goals). Strong foundation.
   - `All day / no rush` → Go as far as feels right, stop when energy drops.

2. **Have you used a note-taking system before?**
   - `Yes, with existing notes to import` → Flag Phase 8 (Import) for later. Ask what system, estimate volume.
   - `Yes, but starting fresh` → Skip Phase 8.
   - `No` → Skip Phase 8, keep things simple.

### Group 2: Scope

3. **Do you need separate vaults for different parts of your life?** (e.g., work vs personal, or different privacy levels)
   - `Yes` → Flag Phase 10 (Multi-Vault) for after the first vault is stable. Don't set up now.
   - `No / not sure` → Skip Phase 10. One vault is simpler and covers most people.

4. **Do you track your health with a wearable?** (Oura, Apple Watch, Whoop, Garmin)
   - `Yes` → Flag Phase 10.5 (Integrations) for a future session. Note the device.
   - `No` → Skip health integrations.

5. **Do you record meetings or calls?** (Granola, Otter, etc.)
   - `Yes` → Flag transcript integration for later.
   - `No` → Skip.

### Group 3: Depth

6. **Are you interested in building your personal history/timeline?**
   - `Yes` → Include Phase 6 (History).
   - `Not now` → Defer Phase 6.

7. **Do you have 5+ people you want to keep notes about?**
   - `Yes` → Include Phase 7 (People).
   - `Not yet` → Defer Phase 7.

8. **Do you journal or want to start?**
   - `Yes` → Set up Daily Notes in Phase 4.
   - `Maybe later` → Defer daily reflections.

### After the questionnaire

Create a setup plan based on answers:

```markdown
## Setup Plan

### Today
- [ ] Phase 0: Technical Foundation
- [ ] Phase 1: Discovery
- [ ] Phase 2: Framework
- [ ] Phase 3: Conventions
[+ whatever time allows]

### Next session
- [ ] [deferred phases]

### Later (when vault is stable)
- [ ] [integrations, multi-vault, etc.]
```

Save this plan to `_claude/TODO.md` so it persists.

---

## Prerequisites

Before starting, make sure:

1. **Obsidian** is installed and a vault is created (even if empty)
2. **Claude Code** is installed and working
3. **Git** is initialized in the vault directory (`git init` if not). Git is strongly recommended — Claude makes changes directly to files, and git gives you rollback safety. If you don't use git, consider at least backing up before starting.
4. **kepano/obsidian-skills** are installed — copy them to `.claude/skills/` in the vault. These teach Claude correct Obsidian syntax (wikilinks, callouts, frontmatter, Bases, Canvas). Get them from: https://github.com/kepano/obsidian-skills
5. **Obsidian CLI** (v1.12+) is installed for vault interaction from terminal (optional but recommended)
6. Allocate **2-3 hours** for the first session. You won't finish everything, but you'll have a working foundation.

---

## Phase 0: Technical Foundation

**Goal:** Set up the files that make Claude Code effective across sessions.

### 0.1 — Create `.claude/` directory structure

```
.claude/
├── skills/           # kepano/obsidian-skills go here
├── settings.json     # Claude Code settings (auto-created)
└── ...
```

> **Skills limitation:** Claude Code only scans `~/.claude/skills/` (global) and `<project>/.claude/skills/` (project-level). Skills placed in intermediate directories (e.g., `~/Obsidian/.claude/skills/`) are NOT loaded. Place all skills in one of these two locations.

### 0.2 — Create a starter CLAUDE.md in vault root

This is the most important file. It tells Claude Code how to behave in this vault. Start minimal — you'll expand it as the vault takes shape.

```markdown
# [Vault Name] — Project Context

## Vault Purpose
[Will be filled after Phase 1]

## Language
[Primary language for notes. Can be mixed.]

## Conventions
- Use [[wiki links]] for internal references
- Frontmatter is YAML, always preserve existing fields
- Dates in ISO format: YYYY-MM-DD
- Never modify files inside .obsidian/
- Never delete files without explicit confirmation

## Git Workflow
- Commit messages: "type: description" (e.g., "add: weekly review", "edit: goals update")
- Do NOT commit .obsidian/ config changes
- Add .obsidian/ to .gitignore
```

### 0.3 — Create a global `~/.claude/CLAUDE.md` (if doesn't exist)

This file applies to ALL projects, not just the vault. Include:
- Your name and short name (so Claude addresses you naturally)
- Communication style preferences (direct? detailed? challenge assumptions?)
- Language preferences
- What you never want (generic advice? process narration? asking permission for reads?)

> **How the walk-up chain works:** Claude Code reads ALL `CLAUDE.md` files from your current directory up to `~`. So `~/.claude/CLAUDE.md` (who you are) + vault `CLAUDE.md` (how this vault works) compose into one context. Keep identity in the global file, project conventions in the vault file. They stack, not replace.

### 0.4 — Set up `.gitignore`

```
.obsidian/
.trash/
.DS_Store
```

### 0.5 — Set up auto-memory

Claude Code has persistent memory at `~/.claude/projects/<project-path>/memory/`. Create a `MEMORY.md` there. Claude will update it across sessions to remember context, decisions, and patterns. Keep it under 200 lines (Claude sees the first 200 lines automatically).

### 0.6 — Understand the environment model

You don't need to set this up now. But understanding the architecture early saves confusion later.

**Your Claude configuration has three layers:**

```
Layer 1: Person (~/.claude/)
  Who you are, style, universal preferences. Goes with you everywhere.
  Source: a dotfiles repo (git), symlinked into ~/.claude/

Layer 2: Domain (intermediate CLAUDE.md files)
  Domain conventions. Claude reads ALL CLAUDE.md files upward from CWD to ~.
  Example: ~/Obsidian/CLAUDE.md — shared rules for all vaults in this directory.

Layer 3: Project (vault's CLAUDE.md + .claude/)
  Vault-specific: protocols, permissions, skills, commands.
```

**Why this matters:** Your global `~/.claude/CLAUDE.md` (who you are) + vault `CLAUDE.md` (how this vault works) compose into one context automatically. Keep identity in the global file, conventions in the vault file. They stack, not replace.

**When you'll want more:**

| Need | What to add |
|------|-------------|
| Same setup on a second machine | Dotfiles repo: CLAUDE.md + rules + skills + hooks, git-synced |
| Calendar/health/voice data flowing in | Data pipelines: sync scripts + scheduled agents + `_inputs/` |
| Automated daily checks or reports | Cron jobs: LaunchAgents (macOS) or systemd timers |
| Session continuity across machines | Session hooks: auto-naming, briefings, offboarding checklists |

All of this is covered in [claude-environment](https://github.com/dkushnikov/claude-environment) — the infrastructure layer that complements this content wizard. Start with the vault, add environment when you outgrow a single machine.

---

## Phase 1: Discovery — Who Are You?

**Goal:** Understand the person deeply enough to build a structure that fits THEM, not a template.

**Critical principle:** The vault structure must emerge from the person's actual life, not from a productivity framework. Frameworks (PARA, Zettelkasten, Johnny Decimal) are tools, not answers. Ask first, categorize later.

### Questions to ask (conversational, not interrogation)

**Identity & context:**
- What do you do? (work, role, industry)
- What matters to you outside of work?
- What are you trying to figure out or improve right now?
- Do you have a partner? Kids? Dependents?
- Where do you live? Is location stable or changing?

**Knowledge management history:**
- Have you used any note systems before? (Notion, Evernote, Apple Notes, paper)
- What worked? What didn't?
- Do you have existing notes/content to import? How much?
- What's the main pain point that brought you to Obsidian?

**How you think:**
- Do you think in categories or in connections?
- Do you prefer structure (folders, hierarchies) or flat + search?
- Are you a collector (save everything) or a curator (save selectively)?
- Do you journal or reflect regularly?

**Goals & aspirations:**
- Do you have explicit goals? Written down?
- Do you track habits or routines?
- Are there people in your life you want to track notes about?

### What to listen for

- **Life domains** — the natural categories of their life (work, health, family, hobbies, finances...). These become areas.
- **Recurring themes** — what keeps coming up? These become priority areas.
- **Decision points** — what are they actively deciding? These become projects.
- **Knowledge gaps** — what do they want to learn? These feed the learning area.
- **Pain points** — what's causing friction? This informs what to build first.

### Artifact: `_meta/Me.md`

After the conversation, create a "self-portrait" note. This is the vault's anchor — everything connects back to who they are.

```markdown
---
created: YYYY-MM-DD
origin: session
tags:
  - meta
---

# Me

## Who I am
[2-3 paragraphs: role, identity, what defines them beyond their job]

## What matters to me
[Values, priorities — in their own words, not abstracted]

## What I'm working on
[Current focus areas, active questions, things in flux]

## Related files
- [[Areas]]
- [[Goals YYYY]]
```

---

## Phase 2: Framework — Life Architecture

**Goal:** Map the person's life into 5-10 areas that cover everything important without overlap.

### How to derive areas

Do NOT copy someone else's framework. Instead:

1. Take everything from Phase 1 and list all distinct domains
2. Merge overlapping ones (e.g., "gym" and "diet" → Health)
3. Separate ones that feel different (e.g., "career development" vs "personal brand" — internal vs external)
4. Check: does every important thing in their life fit into exactly one area?
5. Check: are there areas with nothing in them? Remove those.
6. Aim for 5-10 areas. Less than 5 = too broad, more than 10 = cognitive overload.

### Common patterns (not prescriptions)

Most people land on 5-7 areas. Here are patterns that tend to emerge — use only the ones that are real for this person:

| Pattern | When it applies |
|---------|----------------|
| Health | Almost always relevant — energy, sleep, fitness |
| Relationships | If they care about tracking people and connections |
| Finance | If money management is active, not on autopilot |
| Career | If work identity matters beyond daily tasks |
| Learning | If they're actively building knowledge or skills |
| Creative / Hobbies | If hobbies, art, travel, or side projects are significant |

Some people also have areas for home/environment, inner work (therapy, meditation), or public presence (writing, speaking). These emerge from the discovery conversation — don't suggest them unless the person mentions something that fits.

### The "People" question

People are cross-cutting — a person might be relevant to work, health (gym buddy), and social life simultaneously. Two valid approaches:

1. **People as a cross-layer** — a separate `People/` folder with profiles that link to areas via tags. Works well if you track 10+ people.
2. **People within areas** — each person lives in their primary area. Works if you have few people notes.

Ask the user which feels more natural.

### Artifact: `_meta/Areas.md`

```markdown
---
created: YYYY-MM-DD
origin: session
tags:
  - meta
  - nav
---

# Areas

[Short explanation of what areas are and how they map to this person's life]

| Area | What it covers | Tag |
|------|---------------|-----|
| [Area name] | [What goes here — derived from Phase 1] | `[tag]` |
| ... | ... | ... |

## Related files
- [[Me]]
- [[Goals YYYY]]
```

### Folder structure

Ask the user which naming style they prefer for area folders:

**Option A: Numbered** — predictable sort order in file explorer. Semantic numbering with gaps (e.g., `11`, `12`, `15`). Works well with 7+ areas.
```
00 — Inbox/
11 — Health/
12 — Career/
...
```

**Option B: Plain** — simplest, most readable. Relies on alphabetical sort.
```
Career/
Health/
Learning/
...
```

**Option C: Emoji-prefixed** — visual scanning, personal feel.
```
💼 Career/
🏃 Health/
📚 Learning/
...
```

Whichever style they choose, the full vault structure looks like:

```
[Inbox folder]/                # Unsorted captures
[Area folders]/                # One per life area (5-10 typically)
[People folder]/               # If using cross-layer approach
Reflections/                   # Daily notes, journaling
Goals/                         # Goals, OKRs, reviews
Projects/                      # Active cross-area projects
Templates/                     # Obsidian templates
_meta/                         # Foundation files (Me, Areas, values)
_attachments/                  # Images, PDFs, non-markdown
_inputs/                       # Raw material for import
_claude/                       # Claude's workspace
  TODO.md                      # Cross-session task tracker
  session-logs/                # Session history (continuity backbone)
```

**Why underscored folders:** `_meta/`, `_attachments/`, `_inputs/`, `_claude/` sort to the bottom and signal "infrastructure, not content."

**`_claude/` subfolders (optional, add when needed):** `drafts/` for work-in-progress notes, `extracts/` for structured data from external sources, `outputs/` for external-facing materials. Start with just `TODO.md` — expand as complexity grows.

---

## Phase 3: Conventions — The Rules

**Goal:** Establish consistent rules so every note is findable and connected.

### 3.1 — Frontmatter standard

Every note created by Claude should include:

```yaml
---
created: YYYY-MM-DD
updated: YYYY-MM-DD
origin: human | claude
tags:
  - [area-tag]
  - [optional topic tags]
---
```

- `origin` tracks who created the note: `human` (user wrote it) or `claude` (Claude created it). Advanced option: add `session` for notes created collaboratively in conversation.
- `tags` are always in frontmatter as a YAML array, never inline
- Tags are lowercase English even if content is in another language

### 3.2 — Tag system

Three layers:

| Layer | Purpose | Examples |
|-------|---------|----------|
| Area tags | Required on every content note | `health`, `finance`, `learning` |
| System tags | For infrastructure | `meta`, `nav`, `goals`, `project/name` |
| Topic tags | Optional cross-area filtering | `travel`, `books`, `cooking` |

Rules:
- Every content file MUST have at least one area or system tag
- Tags are lowercase English
- Projects use hierarchical tags: `project/vault-setup`
- No proliferation — before creating a new tag, check if an existing one fits

### 3.3 — Linking

- Use `[[wiki links]]` everywhere, never `[markdown](links)` for internal references
- Every note should have a `## Related files` section at the bottom with links to connected notes
- Session logs link to all artifacts created in that session
- Goal: the Obsidian graph view should show meaningful clusters, not isolated nodes

### 3.4 — File naming

- File and folder names: user's preferred language, but English is recommended for compatibility
- No date prefixes except for logs and journal entries
- Avoid special characters that break across OS: `/ \ : * ? " < > |`

### 3.5 — What goes where

| Content type | Location |
|-------------|----------|
| New unsorted note | Inbox folder |
| Area-specific note | Respective area folder |
| Person profile | People folder (or area folder) |
| Daily reflection | `Reflections/` |
| Goal or review | `Goals/` |
| Active project | `Projects/` |
| Foundation/identity | `_meta/` |
| Images, PDFs | `_attachments/` |
| Import material | `_inputs/` |
| Claude workspace | `_claude/` (start with `TODO.md`, add subdirs as needed) |

### Update CLAUDE.md

After establishing conventions, expand the vault's CLAUDE.md with all of the above. This is the file future Claude sessions will read — make it comprehensive.

---

## Phase 4: Foundation — The First Notes

**Goal:** Create the seed notes that give the vault its identity.

### Must-have foundation files

1. **`_meta/Me.md`** — self-portrait (from Phase 1)
2. **`_meta/Areas.md`** — area map with descriptions (from Phase 2)
3. **`Goals/Goals [YEAR].md`** — current year goals (from Phase 5)
4. **`Projects/Vault and Workflow.md`** — meta-project tracking vault development itself

### Optional but valuable

- **`_meta/Values.md`** — what they believe in, principles they live by
- **`_meta/My History.md`** — chronological skeleton of their life (see Phase 6)
- **`People/index.md`** — people model + directory of key people
- **`_meta/Psychometrics.md`** — if they've done MBTI, Clifton, DISC, etc.

### Create index files

Each area folder should have an `index.md` that explains what goes there and links to key notes. Keep them minimal — they grow over time.

---

## Phase 5: Goals — What Are You Working Toward?

**Goal:** Capture the user's goals in a structured, connected way.

### How to approach this

This is a conversation, not a form. Don't ask "what are your goals?" — that gets generic answers. Instead:

1. **Start with vision:** "If you could wave a magic wand, what would your life look like in 2-3 years?"
2. **Identify gaps:** "What's the biggest difference between that vision and today?"
3. **Find the theory of change:** "What would need to happen for that gap to close?"
4. **Get specific:** "What could you actually do this year toward that?"
5. **Challenge:** "Is this something you genuinely want, or something you think you should want?"

### Structure the goals doc

```markdown
---
created: YYYY-MM-DD
updated: YYYY-MM-DD
origin: session
tags:
  - goals
---

# Goals [YEAR]

## Vision
[What they're ultimately working toward — not a goal, but a direction]

## Theory of change
[The key levers — what actually drives progress toward the vision]

## By area
### [Area 1]
- [Specific, actionable goals]

### [Area 2]
- ...

## Open questions
[Things they haven't figured out yet — these are valuable to track]

## Related files
- [[Me]]
- [[Areas]]
```

### Key insight from experience

Goals docs are living documents, not contracts. Include an "Open questions" section — the things they're still figuring out are just as important as the things they've decided. Claude should revisit and challenge these in future sessions.

---

## Phase 6: History — Where You Come From

**Goal:** Build a personal timeline that connects past experiences to present identity.

### Why this matters

History isn't nostalgia — it's pattern recognition. Understanding where you've lived, who you've been with, what you've done helps identify patterns that inform current decisions.

### Approach

1. **Start with a skeleton** — `_meta/My History.md` with major life phases
2. **Branch into area timelines** — detailed histories in specific areas (health, relationships, career, housing)
3. **Link them** — use a `timeline` tag to connect all history files

### Structure

**`_meta/My History.md`** — the skeleton:
```markdown
## [Phase name] (YYYY—YYYY)
Where: [location]
Key: [1-2 sentence summary]
See also: [[Area-specific timeline]]
```

**Area timelines** (e.g., `Health/Health Timeline.md`):
- Detailed chronological notes within one area
- Connected to the main skeleton via links

### Don't force this

Not everyone has a strong historical orientation. If the user isn't interested in building their history, skip this phase. It's valuable but not essential.

---

## Phase 7: People — Your Network

**Goal:** Create a system for tracking important people and relationships.

### When to build this

Only if the user has 5+ people they want to track notes about. Otherwise, people notes can live ad hoc in area folders.

### People model

Ask the user to think about the roles people play in their life. Common categories:
- People they learn from / admire
- People who work for them (personal context — coaches, assistants, doctors)
- Close relationships (partner, family, close friends)
- Professional peers
- Mentors

### Profile template

```markdown
---
created: YYYY-MM-DD
updated: YYYY-MM-DD
origin: session
tags:
  - people
  - [relevant area tags]
---

# [Person Name]

## Context
[Who they are, how you know them, why they matter]

## Notes
[Running notes — things to remember, conversation topics, observations]

## Related files
- [[relevant notes]]
```

### People vs Relationships (advanced pattern)

If the user tracks both factual profiles AND emotional/working relationship notes, consider splitting:

- **People/** = reference catalog. One file per person: `First Last.md` (standardized name). Contains: who they are, how you know them, factual context. Aliases in frontmatter for nicknames and other languages.
- **Relationships/** (or within the Relationships area) = working files. Short first name (`Anna.md`, `Tom.md`). Contains: active dynamics, things to discuss, emotional context. Links to the People profile.

This prevents "reference bloat" in relationship notes and keeps profiles clean for cross-area linking. Only worth it if the user has 10+ people AND tracks relationships actively.

---

## Phase 8: Import — Bringing In Existing Content

**Goal:** Migrate existing notes without creating a mess.

### The cardinal rule

**The vault is a working model, not an archive.** Not everything deserves to be imported. A note enters the vault only if:

1. It contains an original thought (not just a bare link or screenshot)
2. It connects to something alive (goals, people, an active area)
3. It's a personal artifact (biography, values, something uniquely yours)

Everything else stays in `_inputs/` as raw material.

### The process

```
Source (Notion, Apple Notes, Evernote, etc.)
  ↓ export
_inputs/[source-name]/          # raw dump
  ↓ triage
Tier 1: Import now              # original thoughts, active references
Tier 2: Enrich later            # good raw material, needs work
Tier 3: Leave as reference      # context only, don't import
  ↓ import tier 1
Respective area folders         # with proper frontmatter, tags, links
```

### Triage tips

- Do triage in batches, not all at once (cognitive fatigue kills quality)
- Claude can help categorize — show it a batch, let it propose tier assignments, you approve
- Create `_inputs/index.md` to track what's been imported and what's pending
- Historical artifacts get an `archive` tag and their own note (don't embed in other files — better for graph connectivity)

---

## Phase 9: Session Lifecycle — Continuity Across Conversations

**Goal:** Set up patterns that make every Claude session build on previous ones. This is what transforms Claude from a tool you use into a partner that accumulates context.

### Session onboarding (what Claude does at session start)

At the start of every session, Claude should:

1. Read CLAUDE.md, MEMORY.md, last session log, and `_claude/TODO.md`
2. Check any cached data (calendar, health — if integrations exist)
3. Show a brief: today's date, last session title + when, stale TODO items, contextual suggestions

You can codify this in `.claude/rules/session-onboarding.md` — a file Claude reads automatically. The brief doesn't need to be fancy. Even "Last session: Goals Deep Dive (3 days ago). 2 TODO items older than a week." changes the conversation quality.

> **Why this matters:** Session 1 and session 10 feel identical without onboarding — Claude starts from zero every time. With onboarding, session 10 opens with "You haven't touched Goals in two weeks, and there's a Victoria session to process." That's a different relationship.

### Session logs

Create a session log at the START of every session:

```
_claude/session-logs/YYYY-MM-DD — Session.md
```

Structure:
```markdown
---
type: session-log
created: YYYY-MM-DD
---

## Topic
[one line — what this session is about]

## What we did
[key results, not process narration]

### Artifacts
| File | What |
|------|------|
| ... | ... |

## Key decisions
[decisions made, with rationale]

## What's next
[next steps, open questions]
```

Rename the file when the theme becomes clear (e.g., `2026-03-01 — Goals Deep Dive.md`).

### Memory system

Claude Code's auto-memory (`~/.claude/projects/.../memory/MEMORY.md`) is the key to continuity. After each session, update it with:

- Vault structure decisions (what folders exist, why)
- Key files and what they contain
- User preferences discovered during the session
- Open questions and next steps
- Conventions that were established

Keep MEMORY.md under 200 lines. For detailed notes, create separate files in the memory directory and link from MEMORY.md.

### Cross-session TODO tracker

Create `_claude/TODO.md` — a task list that persists across sessions. Add a `<!-- since: YYYY-MM-DD -->` marker to each item so Claude can track age:

```markdown
# TODO

## This week
- [ ] Process Victoria coaching notes <!-- since: 2026-03-28 -->
- [ ] Goals 2026 deep review <!-- since: 2026-03-15 -->

## When available
- [ ] Import Apple Notes (23 items) <!-- since: 2026-03-01 -->

## Parked
- [ ] Vipassana research <!-- since: 2026-03-10 -->
```

**Deferral escalation** — Claude checks TODO at session start:

| Age | What Claude does |
|-----|------------------|
| 7-13 days | Soft mention: "This has been in TODO for 10 days" |
| 14-20 days | Direct question: "This keeps getting deferred. Intentional?" |
| 21+ days | Propose: "Remove, park, or schedule a dedicated session?" |

This prevents the TODO from becoming a graveyard of good intentions.

### Repeatable operations → Protocol + Skill

When you find yourself doing the same operation repeatedly (daily reflection, weekly review, goal check), formalize it:

- **Protocol** (`_claude/protocols/...` or `_claude/extracts/.../protocol.md`) — step-by-step procedure: what to read, what to create, what format
- **Skill or command** (`.claude/skills/` or `.claude/commands/`) — one-word trigger for Claude

Example: `/daily-reflection` → reads protocol → checks calendar + health data → creates structured reflection. One command, reproducible every time, by any Claude session.

You won't need this on day one. But after 2-3 weeks, when you notice yourself explaining the same procedure to Claude for the third time — that's the signal to formalize.

### Session offboarding (2-minute end-of-session checklist)

At session end, Claude should:

1. Update `_claude/TODO.md` — close done items, add new ones with `<!-- since: -->` markers
2. Update memory — capture new preferences, decisions, patterns
3. Finalize session log — artifacts table, key decisions, what's next
4. Commit to git — don't let work pile up uncommitted

This can also live in `.claude/rules/` as an offboarding rule. The key insight: **knowledge loss happens between sessions, not during them.** Two minutes of structured closing prevents hours of re-discovery next time.

### What makes sessions productive

1. **Onboarding brief at start** — Claude reads context and shows what matters today
2. **Create the session log early** — don't wait until the end
3. **Commit after meaningful changes** — git is your safety net
4. **Offboarding checklist at end** — TODO, memory, log, commit
5. **Leave breadcrumbs** — the "what's next" section is the most valuable part of any session log

### For episodic users — once the infrastructure is set up

The patterns above assume regular use — daily or near-daily sessions where compound interest works naturally. If you know up front you'll use the vault episodically (a few times a month, or less), the stateful multiplier still works, but requires different habits.

The short version:

- **Brain-dump before complex operations.** Spend 5 minutes writing your current head-context into a note *before* asking Claude to do anything complex. Your head has more than the vault knows, and complex operations on thin context produce plausible but wrong output.
- **Weekly reflection even without a task.** Fifteen minutes once a week, just writing what's on your mind. Keeps the vault from going stale between real sessions.
- **Calibrate memory before serious operations.** Ask Claude "what do you know about X?" before deep work. If the summary is stale, update memory before proceeding.

**Full patterns (with rationale and examples):** see [`guides/session-workflow.md`](guides/session-workflow.md). That guide covers the episodic pattern in depth, plus complex operation priming, anti-patterns, and the "feels like Claude forgot everything" troubleshooting flow.

---

## Phase 10: Multi-Vault Architecture (Optional)

**Goal:** If the user needs separate vaults (personal vs work, or different sensitivity levels), set up isolation and cross-vault communication.

### When to use multiple vaults

- Different sensitivity levels (personal vs work vs private)
- Different git repos / sharing rules
- Content that should never mix (e.g., work HR data and personal journal)

### Cross-vault communication

The core challenge: each vault runs its own Claude Code session. How do they share context without breaking isolation?

**Pattern: Shared directory with context files.**

Create a shared directory (NOT a vault) that each vault symlinks to. Each vault owns one context file summarizing what's relevant for the other vaults. Naming is up to you — the structure matters more than the names.

Key principles:
- Each vault's Claude Code only edits ITS OWN context file in the shared directory
- Never copy content between vaults without explicit instruction
- A top-level `CLAUDE.md` above all vaults defines isolation rules and access topology
- Symlinks make the shared directory visible inside each vault for linking

**Optional: Inter-Claude messaging.** If you run Claude Code in different vaults, they can leave messages for each other through files in the shared directory. Claude in vault A writes a message, Claude in vault B reads it next session. Simple but effective for cross-domain insights.

### Skip this if

The user only needs one vault. Don't over-engineer. A single vault with good folder structure covers most people.

---

## Phase 10.5: External Data Integrations (Optional)

**Goal:** Connect external data sources to the vault for richer context.

### Health data (wearables)

If the user tracks health with a wearable (Oura, Whoop, Apple Watch):

1. **Check for MCP servers** — many wearables have Claude MCP integrations (cloud-based). These let Claude pull live data directly.
2. **Define integration points** — when does health data appear in the vault?
   - Daily reflection (sleep score, readiness in frontmatter + narrative section)
   - Weekly health check (structured analysis note)
   - Morning briefing (verbal summary at session start)
3. **Create a protocol doc** — in the Health area, document what's connected, what data flows where, baseline metrics.
4. **No MCP available?** — Some health platforms don't have MCP integrations yet. Use an export app to sync data to your computer, then place exports in `_inputs/` for Claude to analyze.

### Meeting transcripts

If the user records meetings (Granola, Otter, Fireflies):

1. **Raw transcripts** go to `_inputs/[source]/YYYY-MM-DD — Title.md` with `source:` in frontmatter
2. **Processed notes** go to the relevant area folder — route by topic to whatever areas the user set up in Phase 2
3. **Multi-vault routing** — if the user has separate vaults, define which meetings go where by participant/topic. Personal meetings never bleed into work vaults.

### Calendar analysis

Google Calendar (or other calendar MCP) can provide rich data:
- Time allocation analysis by area/category
- Social pattern detection (who do they meet, how often)
- Travel pattern extraction
- Forward-looking event preparation

Store analysis artifacts in `_claude/extracts/`, actionable insights go into area notes.

---

## Lessons Learned — From Real Experience

Things that worked:

1. **Structure follows life, not theory.** Don't start with a framework and force-fit. Start with "what matters to you?" and let structure emerge.

2. **Vault = working model, not archive.** The biggest mistake is importing everything. Be ruthless about what earns a place in the vault.

3. **Frontmatter is non-negotiable.** Every note needs `created`, `tags`, `origin` at minimum. Without this, the vault becomes unsearchable chaos within weeks.

4. **Links are the point.** The graph view is what makes Obsidian more than a folder of markdown files. Every note should link to related notes. A `## Related files` section at the bottom is the simplest habit to enforce.

5. **Session logs are the backbone.** They provide continuity across Claude sessions and serve as a decision journal. Creating them at the START (not end) of sessions captures context that would otherwise be lost.

6. **Memory keeps Claude useful.** Without MEMORY.md, every session starts from zero. With it, Claude knows your vault, your conventions, your preferences, and your open questions.

7. **Conventions before content.** Spending 30 minutes on frontmatter rules and tag taxonomy saves hours of cleanup later.

8. **Git keeps you safe.** Commit after every meaningful change. Claude sometimes makes mistakes. Git lets you roll back.

9. **Don't build everything at once.** Foundation first (Me, Areas, Goals), then fill in organically as topics come up in conversation.

10. **Challenge, don't just organize.** The best Claude sessions aren't just "file these notes" — they're "here's what I'm thinking, push back on the weak parts."

11. **Never batch-replace wiki links with sed/perl.** The `|` character in `[[link|alias]]` syntax causes catastrophic corruption in regex-based replacements. Always use a dedicated edit tool, one file at a time.

12. **`_claude/outputs/` is not `_claude/drafts/`.** Drafts are internal (will become vault notes). Outputs are external-facing (guides for other people, messages to send, posts to publish). Keep them separate.

13. **Health data integrations compound.** Connecting Oura (or similar) to daily reflections takes 30 minutes to set up but transforms every future session — Claude can say "you slept 5 hours, readiness 52, maybe today isn't the day for a deep strategy session."

14. **Obsidian CLI is powerful but has gotchas.** `property:set` for list fields (like tags) writes comma-separated strings, not YAML arrays. Multi-line JS in `eval` fails — write to temp file first. Always use the Edit tool for frontmatter, CLI for reads and searches.

15. **Session lifecycle is the multiplier.** Onboarding (read context, show brief) + offboarding (update TODO, memory, log, commit) takes 3-4 minutes combined but compounds session over session. Without it, every conversation starts from zero. With it, Claude becomes a partner with a growing model of who you are and what you're working on.

16. **TODO markers prevent drift.** `<!-- since: YYYY-MM-DD -->` on every TODO item lets Claude track age and escalate. Without markers, tasks silently age until they're forgotten or irrelevant. With markers, Claude asks "this has been deferred for 3 weeks — intentional?" That question alone is worth the 5 seconds of adding the marker.

17. **Context in your head compounds faster than the vault.** For users with any gap between sessions — a few days, a week, more — your mental context about recent events runs ahead of what the vault has seen. If you skip straight to a complex operation without priming Claude, you'll get plausible-but-thin output because Claude is working with stale input. The fix is a 5-minute brain-dump into `_inputs/` before any serious operation — see `guides/session-workflow.md` for the full pattern. Learned from episodic-user feedback: the tool is fine, the pattern is missing.

---

## What's Next — Beyond the Foundation

The vault you've built is a foundation. Here's where it leads.

### Knowledge Store

Your vault is for YOUR thinking — original thoughts, goals, reflections, decisions. But you also consume external knowledge: articles, books, podcasts, ideas from conversations. Where does that go?

Not in your vault. An article about sleep optimization isn't your thought about sleep — it's raw material. Mixing external sources with your own thinking muddies both.

The answer is a companion vault: a **Knowledge Store** for external sources, with AI-assisted extraction (summarize, tag, cross-reference) and federated search across your vaults. AI does the filing. You do the understanding. The boundary matters — delegating filing is efficient, delegating understanding is self-deception.

A companion seed for Knowledge Store setup is planned.

### Work Context: The Missing Layer

Every company investing in AI tools makes the same mistake: they deploy AI at the company level and wonder why adoption stalls. The tools are good. The models are capable. But they're missing the most important input: **the person**.

An AI that knows your company's Confluence but doesn't know your decision-making style, your current priorities, your energy level, your relationship dynamics with specific colleagues — is a search engine with better grammar. It can retrieve information. It cannot exercise judgment.

What makes the vault approach different: Claude knows YOU. Your values (what you optimize for when goals conflict). Your strengths and blind spots (from psychometrics, coaching, self-reflection). Your current state (sleep data, energy, what happened yesterday). Your relationships (who needs what from you, who you trust for what).

When it helps you write a message, it writes it the way YOU would — not corporate average. When it prepares for a meeting, it knows what YOU care about beyond the agenda. When it reviews your week, it sees patterns across health, work, relationships, and goals that no single-domain tool can see.

**Company AI + Personal context = the combination that actually works.** Neither alone is sufficient. The company layer has the operational data — documents, tickets, channels. The personal layer has the judgment — values, priorities, relationships, energy. An AI with both layers doesn't just retrieve and summarize. It thinks with you.

This is not a feature of any particular tool. It's a thesis about how AI collaboration should work: **context about the person is not optional, it's the primary input.** The vault is your personal context layer — portable, private, yours.

We're exploring this further under the working title **Personal AI**.

### Beyond the vault — separating identity from substrate

Once your vault stabilizes — typically after a month or two of regular use and a refined `Me.md`, `Areas.md`, `Goals.md` — you may notice a different boundary emerging. *"Who I am"* becomes more stable than *"what's in the vault."* Your identity stops needing the vault to hold it. Your Soul, your roles, your values, your working style — these want to be separable from any particular substrate, any particular tool.

That's a different project. Not part of this seed. Substrate-agnostic by design. Found separately by those who look for it.

If you reach that boundary — you'll know.

---

## Quick Start Checklist

For the impatient — the minimum viable setup:

- [ ] Git init + .gitignore (exclude .obsidian/)
- [ ] Install kepano/obsidian-skills in .claude/skills/
- [ ] Create minimal CLAUDE.md in vault root
- [ ] Create ~/.claude/CLAUDE.md with personal preferences
- [ ] Run Phase 1 discovery conversation with Claude
- [ ] Create _meta/Me.md
- [ ] Create _meta/Areas.md + folder structure
- [ ] Establish frontmatter + tag conventions (update CLAUDE.md)
- [ ] Set up session continuity: `_claude/TODO.md` (with `<!-- since: -->` markers) + `_claude/session-logs/` + MEMORY.md
- [ ] Create first session log (do this NOW — not at end of session)
- [ ] Set up session onboarding rule in `.claude/rules/` (even a simple one: read last log + TODO)
- [ ] Create Goals/Goals [YEAR].md
- [ ] Commit everything
- [ ] Start using the vault

Everything else can be built incrementally across sessions.

---

## Recommended Obsidian Plugins

Core (built-in, just enable):
- **Templates** — for note templates
- **Daily notes** — for reflections
- **Backlinks** — essential for graph navigation
- **Graph view** — visual connections
- **Tags** — tag pane for browsing
- **Outgoing links** — see what a note links to

Community (install via Community Plugins):
- **Dataview** — query notes like a database (powerful with good frontmatter)
- **Templater** — advanced templates with dynamic content
- **Calendar** — visual calendar for daily notes
- **Obsidian Git** — auto-commit and backup (alternative to CLI git)

---

## Recommended Claude Code Setup

### CLAUDE.md structure (final state)

```
CLAUDE.md (vault root)
├── Vault Purpose
├── Structure (folder tree with descriptions)
├── Tag System (layers, rules, examples)
├── Frontmatter Conventions
├── Session Logs (format, triggers)
├── Graph Connectivity (linking rules)
├── Language Rules
├── Git Workflow
├── Claude Workspace (_claude/ usage)
└── Conventions (naming, inbox, attachments)
```

### Memory structure

```
~/.claude/projects/<path>/memory/
├── MEMORY.md          # Main memory (< 200 lines)
├── vault-setup.md     # Detailed vault structure notes
└── [topic].md         # Topic-specific deep notes
```

### MCP integrations

Claude Code can connect to external services via MCP (Model Context Protocol). Useful personal integrations:

| Service | What it gives you |
|---------|------------------|
| **Oura Ring** | Sleep, readiness, HRV, stress, workouts — live data in reflections |
| **Google Calendar** | Event analysis, time allocation, social patterns, travel extraction |
| **Gmail** | Search correspondence, draft emails based on vault context |
| **Granola** | Meeting transcripts — pull, route, and process into vault notes |
| **Notion** | If migrating from Notion — read databases, pages, extract content |
| **Slack** | Read channels, search messages, draft announcements |

MCP servers are cloud-based integrations configured through Claude settings, not local CLI tools.

### Hooks and skills

- **kepano/obsidian-skills** — Obsidian syntax (wikilinks, callouts, frontmatter, Bases, Canvas)
- **Obsidian CLI skill** — if using Obsidian CLI for vault interaction
- **Session start hook** — can auto-display date, last session info (e.g., show today's date + last session title)

---

*This wizard was distilled from building a real personal vault over multiple sessions. The process is iterative — don't try to finish in one sitting. Build the foundation, then grow organically.*
