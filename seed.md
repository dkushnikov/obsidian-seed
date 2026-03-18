<!-- seed v2026.03.18 -->
# Obsidian Vault Setup Wizard — Claude Code Edition

> This is a step-by-step guide for Claude Code to help a user build a personal Obsidian vault from scratch. Place this file in your vault root or `.claude/` directory, open Claude Code, and say "let's start" or reference this file.
>
> Based on a real multi-session vault build. The process works — but only if Claude asks, not assumes.

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

### 0.4 — Set up `.gitignore`

```
.obsidian/
.trash/
.DS_Store
```

### 0.5 — Set up auto-memory

Claude Code has persistent memory at `~/.claude/projects/<project-path>/memory/`. Create a `MEMORY.md` there. Claude will update it across sessions to remember context, decisions, and patterns. Keep it under 200 lines (Claude sees the first 200 lines automatically).

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
  Session Logs/                # Claude session logs
Projects/                      # Active cross-area projects
Templates/                     # Obsidian templates
_meta/                         # Foundation files (Me, Areas, values)
_attachments/                  # Images, PDFs, non-markdown
_inputs/                       # Raw material for import
_claude/                       # Claude's workspace
  TODO.md                      # Cross-session task tracker
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

## Phase 9: Session Workflow — Continuity Across Conversations

**Goal:** Set up patterns that make every Claude session build on previous ones.

### Session logs

Create a session log at the START of every session:

```
Goals/Session Logs/YYYY-MM-DD - Session.md
```

The separator between date and title is a style choice (dash, em dash, colon — whatever feels natural). Pick one and stay consistent.

Structure:
```markdown
---
created: YYYY-MM-DD
origin: session
tags:
  - goals
  - project/vault-setup
---

# YYYY-MM-DD — Session

## What we did
- ...

## Key decisions
- ...

## Artifacts created
| File | What it is |
|------|-----------|
| ... | ... |

## What's next
- ...

## Related files
- [[...]]
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

Create `_claude/TODO.md` — a simple task list that persists across sessions:

```markdown
# TODO

## Waiting for user
- [ ] Item description → what Claude will do once received

## Waiting for Claude
- [ ] Task description (when conditions are met)
```

Claude checks this at session start and updates during/after sessions. It bridges the gap between session logs (historical) and active work.

### What makes sessions productive

1. **Read context first** — at session start, Claude should read CLAUDE.md, MEMORY.md, and the last session log
2. **Create the session log early** — don't wait until the end
3. **Commit after meaningful changes** — don't let work pile up uncommitted
4. **Update memory at session end** — capture what was learned
5. **Leave breadcrumbs** — the "what's next" section in session logs is the most valuable part

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
- [ ] Create Goals/Goals [YEAR].md
- [ ] Create first session log
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
