# Session Workflow — Working with Claude in Your Vault, Day to Day

**This guide is for after setup. You've run the wizard, your vault exists, the stateful multiplier is in place. Now: how do you actually use this thing session after session?**

> **Related:** seed.md Phase 9 covers the *setup* of session lifecycle infrastructure (onboarding rule, offboarding rule, memory, TODO with age markers). This guide covers the *ongoing use* of that infrastructure — how sessions actually feel, what patterns make them work, and how to handle the most common failure modes. If you haven't set up Phase 9 yet, go back to seed.md first.

---

## The session rhythm

A session has three phases — open, work, close. Each is short. Together they're the difference between a vault that feels alive and a vault that feels like a graveyard of good intentions.

### Open (2 minutes)

You open a terminal in your vault directory, run `claude`, and wait for Claude to show its session brief.

Claude reads:
- `CLAUDE.md` — vault conventions and structure
- `MEMORY.md` — persistent decisions and context
- Most recent session log(s) — what you worked on last time
- `_claude/TODO.md` — open items, with age markers flagged

Then it shows you a brief. It looks something like this:

> Last session was "Goals deep dive" — 3 days ago. You left off saying you needed to think about Q2 priorities.
>
> Two TODO items have been open for more than a week: "process Victoria coaching notes" (10 days) and "re-read Strengthsfinder report" (8 days).
>
> Anything you want to carry forward from last session, or should we start fresh?

**Your job in the open phase:** read the brief. Decide what today is about. Say it out loud to Claude.

Not "help me be productive." Specific: *"I want to finish the Q2 priorities I started last time. Let's open Goals 2026 and pick up where we left off."*

### Work (variable — 20 min to 2 hours)

This is the meat of the session. You do the thing you came to do. Along the way:

- **Ask specific questions.** Generic questions get generic answers. The more you can frame your question in terms of what's already in your vault, the better.
- **Let Claude push back.** If it asks a clarifying question, answer honestly. If it disagrees, consider the disagreement before overriding it.
- **Commit after meaningful changes.** You don't have to stop and commit every five minutes, but don't let an hour of work sit uncommitted. Git is your undo button.
- **Don't batch everything into one ask.** Three focused asks produce better output than one giant "help me with everything."

### Close (2 minutes)

At the end of the session, before you close the terminal, do the closing ritual:

1. **Update `_claude/TODO.md`** — mark done items done, add new ones that emerged with `<!-- since: YYYY-MM-DD -->` markers
2. **Update `MEMORY.md`** — capture any decisions, preferences, or patterns that future sessions should know about. Not every small thing. Just the "if you forgot this, the next session would be worse" stuff.
3. **Finalize the session log** — fill in the artifacts table, the key decisions, and the "what's next" section
4. **Commit everything to git** — one commit at session end, descriptive message

Two minutes. Not a chore. It's the **single highest-leverage habit** in this whole system.

**Why closing matters more than opening:** the open phase is Claude catching up to you. The close phase is you handing context forward to the next session. If you skip the close, the next session is stuck with stale context — and compound interest breaks.

---

## If you use the vault episodically

Here's the honest truth about compound interest: it works best with regular use. Daily or every-other-day, your vault feels alive. Once a week, it feels slightly behind. Once a month, it feels stale — and if you're not careful, you'll conclude "this tool doesn't work for me" when what's actually broken is the frequency.

**You are not broken. Episodic use is a valid pattern.** But it requires different habits than regular use.

### The core problem for episodic users

If you use the vault once every two weeks, the vault has two weeks of new context stuck in your head that it doesn't know about. When you come back and try to do something complex — say, ask Claude to help with a major decision — Claude is working with stale data and your current head is full of fresh data that the vault hasn't seen.

The failure mode is silent: Claude produces plausible-looking output that is subtly wrong because its input was thin. You don't notice until later.

### The fix: brain-dump before complex operations

**Before any complex operation, spend 5 minutes dumping your current head-context into a note.**

Example. You've been away from the vault for ten days. You want Claude to help you think through a big decision about your team structure. Instead of opening a session and asking "help me think through team structure," do this first:

1. Open a new note: `_inputs/2026-04-11 — head context for team decision.md`
2. Brain-dump: what's happened since I last wrote? What's on my mind? What new information came in? What's changed? What am I worried about? What do I already suspect the answer is?
3. Save the note.
4. *Then* open the session and say: "Read `_inputs/2026-04-11 — head context for team decision.md`, then let's think through team structure."

Claude now has:
- The full vault (background)
- Your 5-minute brain-dump (current state)
- The specific ask (focused question)

Output quality jumps from "plausible but thin" to "can actually engage with your real situation."

**This works because the cost of brain-dumping is low and the cost of acting on thin context is high.** Five minutes of typing saves an hour of re-work or a bad decision.

### Weekly context refresh (even if you don't use the vault)

If you're strictly episodic — days or weeks between sessions — consider a **weekly reflection ritual** even when you don't have a specific task. Fifteen minutes, once a week:

1. Open `_meta/reflection-journal.md` (create if it doesn't exist)
2. Write what's on your mind this week: wins, frictions, decisions, questions, worries
3. Save and commit

No session with Claude required. This is you talking to your future self — and to your future Claude sessions — without the overhead of a full conversation.

The value: next time you do open a session with a real task, the vault is not as stale, and Claude has context it wouldn't otherwise have.

### Reality-check against memory before deep operations

One more pattern for episodic users: **check Claude's memory before trusting it**.

Claude reads `MEMORY.md` at session start. But `MEMORY.md` may be out of date — decisions you made two weeks ago in your head, but never wrote down. Before a serious operation, ask:

> "Claude, what do you know about [topic]? Summarize from MEMORY.md and recent session logs."

If the summary is stale, correct it before proceeding:

> "That's out of date. Since then, X happened and I decided Y. Update MEMORY.md with that."

Now Claude's memory matches reality. The next complex operation runs on accurate context.

This is a **calibration pass** — quick, cheap, prevents silent-failure operations.

---

## Complex operations — when you need strong context

Some sessions are light (quick lookups, small edits, brief conversations). Some are heavy (strategic planning, multi-agent analyses, significant decisions). The heavy ones need more preparation.

**Signals you're entering a heavy operation:**
- You're about to ask Claude to do something that will take 15+ minutes of its attention
- You're about to make a decision that matters
- You're about to run a multi-step process that depends on earlier steps
- You're going to ask Claude to generate substantial content based on your situation

**For heavy operations, do these extra steps beyond the normal open:**

1. **Brain-dump first** (see above) if you're episodic or if context has shifted
2. **Explicitly name the operation** to Claude: "This is going to be a strategic planning session about X. Before we start, I want to make sure you have the context you need."
3. **Ask Claude what it knows and what it's missing**: "What do you know about X? What would you want to know that you don't see in the vault?"
4. **Fill in the gaps Claude names** before starting the real work
5. **Commit a "pre-operation snapshot" to git** so you can rollback if the operation goes sideways

This adds 10 minutes of overhead. For a 1-2 hour operation, it's worth it. For a 10-minute task, skip it.

---

## When it feels like Claude forgot everything

You come back after some time away. You open a session. Claude seems generic, like the vault doesn't exist. This is the single most common "this tool is broken" feeling.

**First, check these in order:**

1. **Did the session onboarding rule actually run?** Claude should have read CLAUDE.md, MEMORY.md, recent session logs, and TODO at session start. Ask Claude: "What did you read at session start? Summarize." If the answer is thin, the onboarding rule didn't fire — or it's not pointed at the right files.
2. **Is MEMORY.md too long?** If MEMORY.md is over 200 lines, Claude may be skipping or summarizing. Prune or restructure.
3. **Is there a recent session log at all?** If you stopped writing session logs a month ago, Claude has no recent context. The vault exists but the continuity layer is broken.
4. **Are there stale contradictions in memory?** If MEMORY.md says "we decided X" but you've since changed your mind, Claude is working with stale data. Fix the memory.

**If all four are fine and Claude still feels generic:** the issue is usually the current session's ask, not Claude's context. Vague questions get vague answers even with perfect memory. Try again with a more specific framing.

---

## The compound interest curve

Here's the honest shape of what happens over time, assuming regular use:

- **Session 1:** You build the vault. Claude is a smart stranger who just read your Me.md.
- **Session 2-3:** Modest compound. Claude remembers your first session's decisions. Quality is maybe 10% better.
- **Session 5-10:** Noticeable compound. Claude starts connecting dots across sessions. You start experiencing "oh, it remembered that" moments.
- **Session 20-30:** Strong compound. Claude has a working model of how you think. Its pushback starts being useful. Its suggestions start being non-obvious.
- **Session 50+:** Deep compound. The vault feels like an externalized part of your mind. Opening a session is less like starting a conversation and more like picking up a conversation in progress.

If you're not seeing any compound after 10-15 sessions, something in the stateful multiplier is broken. Check session logs, memory, TODO markers, onboarding rule. Usually one of these is stale or missing.

**If you use the vault episodically, this curve stretches.** Session 20 for an episodic user might feel like Session 5 for a regular user. That's the cost of episodic use. The brain-dump-before-complex-operations pattern partially compensates — but it doesn't eliminate the gap.

---

## Anti-patterns — things that look right but don't work

**Batching all your asks into one giant session prompt.** Three focused asks produce better output than one mega-ask. Claude responds to each, but the output is diluted.

**Skipping the closing ritual because "I'll do it tomorrow."** Tomorrow will not close the ritual. The knowledge loss happens between sessions, not during them. Two minutes at the end now saves twenty minutes at the start of the next session.

**Treating MEMORY.md as a diary.** MEMORY.md is short, high-signal decisions and context. If it's becoming a diary, put the diary in `Reflections/` and keep MEMORY.md lean.

**Manually re-explaining your context every session.** If you're doing this, the onboarding rule isn't firing or the session log "what's next" wasn't written. Fix the infrastructure rather than repeating the explanation.

**Asking Claude to "organize my notes."** Too vague. Specific: "I have 12 notes in `Reflections/` that should probably be tagged differently. Here's what I think the tags should be. Let me know if that's off." That Claude can do.

**Trusting stale memory.** See the calibration pass above. Before serious operations, check Claude's context is current.

---

## For reference — the files that make this work

(If any of these are missing, session workflow breaks. Go back to seed.md Phase 9 to set them up.)

- `CLAUDE.md` at vault root — vault orientation for Claude
- `_claude/MEMORY.md` — persistent decisions and context
- `_claude/session-logs/` — running journal of sessions
- `_claude/TODO.md` — task list with `<!-- since: YYYY-MM-DD -->` age markers
- `.claude/rules/session-start.md` — session onboarding rule (what Claude reads at session start)
- `.claude/rules/session-end.md` — session offboarding rule (what Claude does at session end)

Together, these five files are the **stateful multiplier** — the thing that makes session ten feel different from session one. Without all five, the system is partial. With all five, compound interest kicks in.

---

## Accessibility note — voice input

If typing at length is uncomfortable for you, voice-to-text tools like [Wispr Flow](https://wisprflow.ai) turn Claude Code into something you can talk to. This is particularly useful for the brain-dump-before-complex-operations pattern — speaking a 5-minute context dump is often faster than typing it, and for some people the spoken version is more natural and complete. Not a requirement; a quality-of-life unlock for the right audience.
