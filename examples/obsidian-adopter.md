# Example — Obsidian Power User Adopting Seed

**This example follows Chen, an experienced Obsidian user with a vault he's refined over two years. The patterns here — defensive adoption, preserving existing work, selective integration, commitment calibration — apply broadly to anyone with substantial prior Obsidian investment considering whether and how to add seed's methodology without starting over.**

**Chen is fictional. The friction points and the resolution (use `ADOPT.md` not `seed.md`, go section-by-section, git commit per change, preserve existing conventions) are real — observed in multiple existing-vault users who tried seed and either cherry-picked surface features or abandoned the attempt. This example shows what happens when you use the adopt path instead.**

---

## About Chen

Chen is a senior research engineer at a mid-sized tech company. He's been using Obsidian for about two years. Started as a personal knowledge base for papers he was reading, grew into a full work + life vault with 300+ notes, a refined folder structure, Dataview queries driving several dashboards, and a frontmatter schema he designed himself over months of iteration.

His stack: Obsidian, iCloud sync to his phone, daily notes habit (missed maybe 20 days in two years), custom CSS snippets, Templater for new-note templates, Linter for frontmatter normalization, a few community plugins he depends on (Dataview, Advanced Tables, Obsidian Git).

**What works:** his vault is alive. He uses it daily. He finds what he needs. His graph shows him patterns. He trusts it.

**What doesn't (the reason he's looking at seed):** he's been using Claude Code for coding for a few months and noticed something — Claude in the terminal is powerful, but Claude-with-his-vault was... generic. Claude didn't know his conventions. Didn't know what his areas meant. Treated every session like a fresh chat. When he asked for help thinking through a research direction, the output was plausible but not *his*. He wanted the vault-aware, context-accumulating version of Claude that he'd seen a colleague demo.

He read about seed. Saw the section on "stateful multiplier." Recognized the value — session logs, memory, CLAUDE.md, session workflow rules working together. Realized his vault was missing most of that infrastructure.

And then he read the README quickstart and it said *"Create an empty Obsidian vault."*

No.

---

## Why ADOPT.md instead of seed.md

Chen is not going to dump his 300-note vault and start over. The methodology he wants is the stateful multiplier. The content he has is irreplaceable. He needs to **add** seed's infrastructure to his existing vault without touching what he's built.

He scrolled past the main README and found a second file: `ADOPT.md`. The description: *"For users who already have an Obsidian vault and want to add seed's patterns without destroying existing work."*

That was the door.

---

## Step 1 — The intent check

Chen opened a terminal in his vault directory. `claude`. Said: *"Read ADOPT.md and help me adopt seed into my existing vault."*

Claude's first response was not instructions. It was a five-question check-in:

> *"Before we scan anything or propose any changes: what brought you here, and what do you hope to get out of this?"*

Chen gave a short answer: he wanted Claude-with-vault to actually know his vault. He wanted persistent context across sessions.

Claude asked a second question: *"If nothing changes a month from now — is that OK, or is that a failure?"*

Chen thought. Honestly: disappointing but OK. He'd keep using the vault the way he had been.

Claude asked about time budget. An hour, maybe an hour and a half. He wasn't going to marathon this.

Claude asked about his default reaction if seed proposed changing something in his vault. *"Closer to 'let's see what you propose' or 'show me every detail first'?"*

Chen: show me every detail first. He's not going to let an AI tool run wild in his vault.

Claude asked what was missing in his current setup. Chen: the AI collaboration quality. Not the notes themselves.

After the five questions, Claude summarized:

> *"Based on your answers, you sound like general engagement mode — you want this to work, you'll put real time in, but you're cautious about changes to what you've built. Protective of existing structure. You want explicit previews before anything is written. That tracks. I'm going to move slowly, show you everything, commit each change separately in git, and never overwrite your work without asking. Does that match how you want to do this?"*

Chen confirmed.

**Why this step mattered:** a more aggressive user with "transformation driven" intent would have gotten a different flow — bigger merge plan, faster pace. A "low commitment" user would have gotten a scan-only preview, no merge plan at all. By calibrating intent first, Claude avoided proposing changes Chen would have rejected.

---

## Step 2 — The scan

Claude asked permission to scan. Chen said yes. Scan was read-only — no writes, no modifications.

About five minutes of work (Claude reading files). The output was a structured report.

### What Chen already had

**Substrate:**
- [x] CLAUDE.md (vault root) — exists, Chen wrote it himself months ago. Covers his conventions.
- [x] MEMORY.md — exists, from his direct Claude Code use. Partial, not systematic.
- [ ] Session logs — does not exist.
- [ ] TODO with age markers — has a TODO.md but no age markers.
- [ ] Session workflow rules — does not exist.

**Conventions:**
- Frontmatter: his own schema (`created`, `tags`, `type`, `area`, `status`, some custom fields per-type). Consistent, well-enforced by Linter.
- Linking: wiki links, dense graph. Related files section inconsistent.
- Tag system: hierarchical (`area/research`, `area/platform`, `status/active`).
- Folder structure: nine top-level areas, organized around his life.

**Content:**
- 312 notes across nine areas
- Signs of: daily notes pattern, decision log pattern in one area, a reading notes system based on Zettelkasten-ish principles
- `Me.md` exists, covers his values and working style
- `Areas.md` does not exist explicitly but is implicit in folder structure
- `Goals.md` exists, updated quarterly

### What seed would add

Claude organized the proposed additions by value:

**High-value (the gap in stateful multiplier):**
- Session logs directory (`_claude/session-logs/`)
- Session workflow rules (`_claude/rules/session-start.md` and `_claude/rules/session-end.md`)
- Age markers on his existing TODO.md

**Medium-value (CLAUDE.md extensions):**
- Adding a "Session Logs" section to his CLAUDE.md describing the format and location
- Adding a "Session Lifecycle" section referencing the new workflow rules

**Low-value or skip:**
- Seed's recommended frontmatter schema — Chen's is better (more mature, uses Linter enforcement). Keep his.
- Seed's recommended folder structure — Chen's works. Keep his.
- Seed's foundation files (Me.md, Areas.md, Goals.md) — he has Me.md and Goals.md. Areas.md is implicit in his folder structure. Don't add.
- Seed's convention around wiki links vs markdown links — he already uses wiki links. Done.

### What seed does NOT touch

Claude explicitly listed things it would not propose:

- Any of Chen's existing notes
- His custom CSS snippets
- His community plugins
- His Obsidian settings
- His Dataview queries
- His Linter rules

**Claude's summary:** *"Based on what's here, you're missing two things in the stateful multiplier: session logs and session workflow rules. Everything else you've built independently, and in most cases your version is more refined than seed's default. I'd propose adding three files and making two small edits to your existing CLAUDE.md. Everything else stays untouched. Want to see the merge plan?"*

Chen said yes.

---

## Step 3 — The merge plan

Claude presented a staged plan — five items. For each, it would show him exactly what would change, wait for approval, write the file, commit to git, show the commit hash, and move to the next.

### Item 1 — Create `_claude/session-logs/` directory

Preview: empty directory, one README inside explaining the log format.

Chen: *"Show me the README content first."* Claude showed it. About 20 lines, format specification and an example. Chen approved.

Claude wrote the files. `git commit -m "adopt: create session-logs directory"`. Commit `a3f7d91`. Chen nodded.

### Item 2 — Create `_claude/rules/session-start.md`

Preview: a 15-line rule file telling Claude to read CLAUDE.md, MEMORY.md, the last session log, and TODO.md at session start, then show a brief.

Chen: *"My MEMORY.md is partial — will this break?"*

Claude: *"No. If MEMORY.md is thin, the brief just has less to show. The rule doesn't require any specific content, just reads what's there."*

Chen approved. Claude wrote. Commit `b1e4c82`.

### Item 3 — Create `_claude/rules/session-end.md`

Preview: 20-line rule file. At session end, Claude prompts to update TODO, update memory, finalize session log, commit to git.

Chen: *"Will this interrupt me if I want to end a session without all of that?"*

Claude: *"The rule is a suggestion to Claude, not a forced modal. If you say 'we're done' and skip the offboarding, Claude will note that the ritual was skipped in the session log and stop. Your choice each time."*

Chen approved. Commit `c9b2e51`.

### Item 4 — Add age markers to existing TODO.md

Chen: *"Wait. How do you plan to do this? My TODO.md has 40-something items."*

Claude: *"I'll read each item. For ones with a clear creation date (from the surrounding note or the item text), I'll add the correct `<!-- since: YYYY-MM-DD -->` marker. For ones where I can't tell, I'll mark today's date and note that in the commit message. You can adjust any that are wrong. I'll show you the full diff before writing."*

Chen: *"OK, show me the diff."*

Claude produced a diff. 44 items, ages spanning 3 days to 4 months. About 12 had ambiguous dates — Claude proposed today's date and flagged each. Chen corrected 3 of the 12 to known older dates. Approved the rest.

Commit `d7f38a2`. Commit message noted which items had estimated dates.

### Item 5 — Edit existing CLAUDE.md to reference session lifecycle

Chen: *"Show me the diff."*

Claude proposed a new section in Chen's CLAUDE.md titled "Session Lifecycle" that referenced the new rule files. 14 lines, appended to the end of CLAUDE.md (not modifying existing sections).

Chen read the proposed addition. Approved without changes.

Commit `e4c91f5`.

### After Item 5

Claude paused: *"Five items applied. Any of them you want to revert? Now is the time — I can `git revert` any commit cleanly."*

Chen took five minutes to review each. All five looked right. *"No, keep everything."*

---

## Step 4 — The stateful multiplier check

Claude ran a final verification:

- [x] CLAUDE.md exists and is tailored to his vault
- [x] Memory system present
- [x] Session logs directory present (now)
- [x] TODO with age markers (now)
- [x] Session workflow rules (onboarding + offboarding, now)

**5 of 5.** Full stateful multiplier in place.

Claude's summary: *"You now have the full stateful multiplier. Your existing content, conventions, and plugins are untouched. Five git commits are reversible individually if anything turns out wrong. Next session will start with the new onboarding rule — Claude will read your vault state and show you a brief before you do anything. Give it a try tomorrow."*

Chen closed the session. Total elapsed time: 75 minutes.

---

## His vault after adopt

Nothing visibly changed in the folder structure Chen uses daily. His daily notes still open in the usual place. His Dataview dashboards still work. His Linter still normalizes frontmatter. His custom CSS still applies.

What's different:

- `_claude/session-logs/` — new directory with README
- `_claude/rules/session-start.md` — new file
- `_claude/rules/session-end.md` — new file
- `_claude/TODO.md` — existing file, now with age markers on all items
- `CLAUDE.md` — existing file, now with one new section ("Session Lifecycle") at the bottom

Five changes total. Each in its own commit. `git log` shows exactly what happened.

---

## First session after adopt

Next day. Chen opened the vault for his usual morning session — processing research papers from a reading list.

He typed `claude`. Claude's first response was the new session brief:

> *"Yesterday's session: adopt setup, 5 commits. No session log recorded (adoption was the work). TODO has 44 items with age markers. 3 items older than 21 days — you may want to review those. Ready for today?"*

Chen noticed the three stale items. Two he decided to delete (no longer relevant). One he scheduled. Then he did his usual research processing.

At session end, Claude asked: *"Usual closing ritual? Update TODO, memory, session log, commit?"*

Chen said yes. Two minutes. Session log created. Memory updated with one new decision.

Session 2 the next day opened with a richer brief.

---

## What Chen learned

**/adopt mode speaks his language.** The core language is: "show me, don't do." Every step previewed, every change approved, every commit separate. This matched his mental model of "managing my vault carefully." He never felt like the tool was running ahead of him.

**Git commits per step made him trust the process.** Even for small changes like adding age markers, seeing a clean `git log` with descriptive commit messages meant he could roll back any single step without losing the others. That separability is what made him OK with letting a tool touch his vault at all.

**He got the stateful multiplier without starting over.** This was the whole point. His two years of work, his conventions, his graph — all intact. The new layer (session continuity infrastructure) integrated without conflict. The gap he came to fix was fixed, and nothing else was damaged.

**His existing CLAUDE.md was respected.** Claude proposed an addition to it, not a replacement. The new "Session Lifecycle" section sits at the end of his existing CLAUDE.md. When he edits CLAUDE.md later, he edits his work plus seed's additions as one file — but the boundaries are clear from git history.

**The adopt path is slower than seed path, and that's appropriate.** He spent 75 minutes on adoption. A clean-start user with seed.md would have spent similar time but with more imposed structure. Chen spent it more carefully, on fewer changes, with more review — which is right for someone adding to existing work rather than starting fresh.

---

## Where Chen hit friction (minor)

- **Step 1 felt like a questionnaire.** The intent check's five questions are the same for everyone. Chen wasn't sure why he had to answer them when he's an experienced user. Claude's explanation ("calibration determines the flow") made sense in retrospect but felt bureaucratic in the moment.
- **Step 4 TODO age markers took longer than expected.** 44 items × some judgment on each = 15 minutes. Chen would have preferred a "mark everything as today, I'll fix manually later" option. The tool doesn't offer that shortcut (and the tool author would argue that defeats the purpose — age-tracking only works if ages are accurate).
- **His partial MEMORY.md didn't get upgraded.** Adopt mode explicitly doesn't touch memory. Chen thought about asking Claude to help him consolidate his partial memory, but decided to do that manually later — memory is personal, and he wanted to be the one writing it.

None of these were blockers. They were pace-of-operation feelings. Worth noting for other adopters.

---

## Where Chen did NOT hit friction

- No overwrites of his work
- No plugin conflicts (Linter didn't fight with seed's frontmatter conventions because seed didn't propose changing his frontmatter)
- No surprise structural changes
- No pressure to rename anything or restructure folders
- No imposition of seed's opinionated defaults (capitals, life areas, etc.)

This is the design. Adopt mode is supposed to be respectful by construction. It was.

---

## Is this example for you?

**Read this and try ADOPT.md if:**

- You have an existing Obsidian vault you care about
- You've refined your own conventions over months or years
- You want the stateful multiplier but NOT a restart
- You'll only adopt a tool that previews every change
- You value git reversibility

**This probably isn't what you need if:**

- Your vault is less than a month old and still unstable — just use `seed.md` clean-start
- You're willing to start fresh — seed.md is faster for clean starts
- You want deep methodology coaching, not just infrastructure — adopt is intentionally minimal, seed.md is richer methodology
- You want to use seed's opinionated conventions even though you've built your own — adopt explicitly preserves your existing conventions

---

## Notes

Chen is fictional. His specific vault setup (Dataview queries, custom Linter rules, two years of refinement) is representative of real Obsidian power users but is not anchored to a particular person. The adoption flow described — intent recognition, scan, gap report, staged merge plan with git commits, stateful multiplier verification — is exactly what `ADOPT.md` implements. The friction points and the resolution are based on real observation across multiple existing-vault users who tried seed.

If you're an Obsidian power user considering this and you want to talk through whether adopt mode fits your situation, open an issue on the repo. We read everything.
