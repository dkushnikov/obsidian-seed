# Example — Non-Technical Professional

**This example follows Sarah, a coach. The friction patterns — expecting a proactive AI assistant, struggling with terminal and install, navigating "how personal should I be" in notes — apply broadly to non-technical professionals adapting to AI-assisted tools: consultants, therapists, educators, HR practitioners, and similar service providers with deep expertise in their field but limited exposure to developer tooling.**

**Sarah is fictional. The structure of her vault and her experience with the setup are real patterns — based on friction points we've seen, questions people actually ask, and outcomes that work. If any of the above sounds like you, this is what it looks like from inside.**

---

## About Sarah

Sarah is an executive coach. Fifteen years in the work — first in HR for a multinational, then on her own for the last eight. She runs a solo practice: eight to ten clients at a time, each running six to twelve months. She meets them over video, in person occasionally, and between sessions she takes notes, reads their annual feedback, keeps track of their stated goals, and watches for the patterns they can't see themselves.

Her tools right now: a Google Docs folder per client, a shared calendar, a paid tool for sending pre-session questionnaires, and a lot of mental context that lives only in her head.

**What works:** she's good at her craft. Her clients stay, and they grow.

**What doesn't:** between sessions, she has a hard time remembering the *arc* of each engagement. She'll find a note from three months ago that says "watch for the pattern where she says yes and means no" and realize she hasn't thought about it since. Her Google Docs folders are linear and siloed. Cross-client patterns — the ones her eye can spot at a glance — are invisible in her notes.

She heard about Claude Code and Obsidian from another coach in her peer group. She was skeptical. Most "productivity tools" feel like someone else's filing cabinet glued onto her practice. But when she saw her colleague's setup, one thing stuck: the tool *asked questions* about how she thought, and then built the structure from her answers. That was different from anything she'd tried.

---

## Why she came to seed

Three reasons, in order:

1. **She wanted memory.** Not a database — a way to remember her clients' arcs without having to re-read every note before every session. Something she could ask, not something she had to search.
2. **She wanted reflection.** Her own practice was becoming harder to see. She was good at reflecting *on* her clients and bad at reflecting on *her own work with* her clients. A vault might help.
3. **She was curious.** That's the honest answer. She heard this wasn't like other tools, and she wanted to find out how.

What she was **not** looking for: a productivity system. She's not short on discipline. She's short on *visibility* into her own practice.

---

## What happened in her first session

Sarah was anxious about the technical setup. Her colleague had sent her a link to Obsidian, a link to Claude Code, and a link to the seed file. She installed Obsidian, managed to get Claude Code running after one call to her colleague, and opened a terminal in the vault directory for the first time in her life.

She typed `claude`, and then felt that specific kind of awkwardness you feel when you're talking to a computer program like it's a person for the first time.

She said: *"Follow the guide in seed.md."*

### The first thing the wizard said

Before any questionnaire, Claude asked her to read a short section called *How Claude Works in This System*. Sarah almost skipped it — the whole point was to save time, right? — but she read it. Five minutes.

The section told her four things she needed to know:

- Claude is **reactive**. It doesn't watch her in the background. Nothing happens until she talks to it.
- The value she gets from Claude is a **function of two things**: what she asks, and what Claude knows about her. Both matter.
- Sessions **compound**. Session one and session ten feel different because of a few simple mechanisms they'd build together — not because the model is "learning" in the magical sense.
- Claude **will** ask questions, push back when her reasoning looks weak, and remember what she tells it. It **will not** contact her, run in the background, or notice changes when she's not actively in a session.

Sarah's reaction, as she remembers it: *"Oh. I was waiting for this thing to be like a junior assistant. It's more like a thinking partner who sits silently until I say something."*

That reframe made the rest of the session click.

### The questionnaire

Three groups of questions, conversational:

**Group 1 — basics.** How much time do you have today? *About an hour.* What's your experience level with this kind of tool? *Almost none.* Language? *English.*

**Group 2 — scope.** One vault or several? *One.* Work only, personal only, or mixed? *Mixed — I want it to cover my practice and my reflections on it, which aren't the same thing.*

**Group 3 — depth.** How comfortable with the terminal? *Uncomfortable.* With git? *Never touched it.* With Obsidian? *Just installed it.*

Based on her answers, Claude offered a plan: **run the discovery, framework, and conventions phases today (about 60 minutes)**; set up session continuity infrastructure; leave goals, history, people, and integrations for later sessions.

She said yes.

### Discovery — who are you?

This was the part Sarah had been afraid of. Telling a computer about her life felt strange for about the first three questions. Then it stopped feeling strange because the questions were good ones:

- *What do you do, in a sentence?*
- *What matters to you outside of work?*
- *What are you actively trying to figure out — in work, in life?*
- *How do you think? In categories, in stories, in connections?*

She answered honestly. Some answers were short, some long. When she said *"I think in people and patterns,"* Claude asked a follow-up: *"Can you give me an example of what 'patterns' means for you?"* She thought for a moment and described how she noticed that her clients often knew the answer before they said they knew — how her work was mostly about getting them to hear themselves.

Claude used that answer later in the session, when proposing her folder structure. It suggested a folder called `Patterns/` alongside `Clients/` and `Reflections/`. Sarah hadn't asked for it, but when she saw it, it was right.

### Framework — what are your areas?

From her answers, Claude proposed seven life areas:

- `Practice/` — the coaching work itself
- `Clients/` — individual client notes (inside, one folder per client)
- `Patterns/` — cross-client observations, unnamed things she's noticed
- `Reflections/` — her own reflections on her work and her life
- `Learning/` — books, courses, methodologies she's exploring
- `Relationships/` — non-client people (family, peers, mentors)
- `Health & Energy/` — she had mentioned this mattered to her

She refined this. She moved `Patterns/` to be a subfolder inside `Practice/`, because to her they belonged together. She added `Money/` because she realized it mattered and she'd been avoiding thinking about it. She removed `Health & Energy/` for now, with a note to add it back when she was ready.

What felt different from every template she'd seen: she wasn't fitting her life into the structure. The structure was a draft of her life, and she was correcting it.

### Conventions — the rules

Claude proposed three non-negotiable conventions:

1. **Frontmatter on every note** — at minimum `created`, `tags`, `origin`. Sarah didn't know what frontmatter was. Claude explained: "A small header at the top of each note with standardized info — so you can find things and so I can understand your notes without reading every line."
2. **Wiki links, not markdown links.** `[[Name]]` instead of `[Name](./Name.md)`. Why: the graph only works with wiki links.
3. **A `## Related files` section at the bottom of every note.** A habit, not a rule. The simplest thing that makes the graph rich.

Sarah didn't fully understand the second and third yet, but she trusted that they'd matter later. Claude promised to remind her when they did.

### Foundation — her first notes

At the end of the session, Sarah had three foundation files:

- `_meta/Me.md` — a short document about who she is, what matters to her, what she's working on. She wrote it with Claude's help in about ten minutes.
- `_meta/Areas.md` — her seven areas with one-line descriptions each.
- `_meta/Goals.md` — deferred to next session, with a placeholder.

She also had four infrastructure files she didn't write herself, but Claude set up for her:

- `CLAUDE.md` at the vault root — telling Claude how her vault works
- `_claude/MEMORY.md` — Claude's persistent notes (empty so far)
- `_claude/TODO.md` — her task list with age markers
- `_claude/session-logs/2026-04-11 — Setup.md` — a log of this session

And a folder called `.claude/rules/` with two short rules: one for session start (read context, show brief) and one for session end (update TODO, memory, log, commit).

This — CLAUDE.md, memory, session logs, TODO with markers, session rules — is the **stateful multiplier**. Sarah didn't know the name at the time. She just knew Claude called it "the thing that makes future sessions build on this one."

She closed the terminal after about 75 minutes. She had a working vault. She still didn't know how to use it beyond what she'd just done.

---

## Her vault after setup

```
SarahVault/
├── CLAUDE.md                    # "How this vault works" — for Claude to read
├── _meta/
│   ├── Me.md                    # Who I am (short, honest)
│   ├── Areas.md                 # My 8 areas
│   └── Goals.md                 # Placeholder for next session
├── Practice/
│   ├── README.md                # What this area is about
│   └── Patterns/                # Cross-client observations
├── Clients/                     # One folder per client (empty for now)
├── Reflections/                 # Personal reflections on practice and life
├── Learning/                    # Books, courses, methodologies
├── Relationships/               # Non-client people
├── Money/
├── _claude/
│   ├── MEMORY.md                # Claude's persistent notes
│   ├── TODO.md                  # Task list with age markers
│   └── session-logs/
│       └── 2026-04-11 — Setup.md
├── .claude/
│   └── rules/
│       ├── session-start.md     # Read context + show brief
│       └── session-end.md       # Update TODO + memory + log + commit
└── .gitignore
```

**What `Me.md` looked like after her first session:**

```markdown
---
created: 2026-04-11
tags: [meta, me]
origin: session
---

# Me

I'm an executive coach. Fifteen years. Solo practice for the last eight.
I work with eight to ten clients at a time. Six to twelve month engagements.

## What matters to me

- My clients getting to hear themselves
- My own ongoing reflection on the craft
- Time with my family and space for the work that matters
- Not turning my practice into a production line

## How I think

In people and patterns. I notice before I can explain what I've noticed.
Sometimes I don't know what I know until I say it out loud.

## What I'm working on

- Building a practice that's sustainable, not just successful
- Noticing my own patterns the way I notice my clients'
- Getting better at reflecting on my own work (this is why I'm here)

## Related files

- [[Areas]]
- [[Goals]] (coming next session)
```

Short. Honest. Nothing performative. This is the foundation every future session builds on.

---

## Lessons from Sarah's first week

### What the wizard did well

- **It asked questions before it proposed structure.** By the time it offered folders, she had already answered enough that the folders felt like a draft of her, not a template for her to fit into.
- **It explained Claude reactivity upfront.** Without that five-minute *How Claude Works* read, she would have expected autonomous behavior and been disappointed when nothing happened between sessions.
- **It set up the stateful multiplier as a package.** Sarah didn't know why CLAUDE.md or MEMORY.md or session logs or the TODO markers mattered individually. She just trusted that they worked together and would reveal their value later. They did.
- **It refused to impose.** When she moved `Patterns/` into `Practice/`, Claude didn't argue — it updated everything else to match.

### Where she hit friction

- **The first few terminal commands were scary.** She needed her colleague on a call to get past `git init` and `claude` on first run. **This is a real gap for non-technical users.** If you're in Sarah's spot, you may want to ask someone technical to help with the very first install, or wait for a dedicated setup guide.
- **Conventions felt bureaucratic at first.** "Frontmatter on every note, related files section, wiki links only" — she didn't feel the value until she had 20 notes and tried to find one. Then she got it. The wizard warned her this would happen, and it did.
- **Her discovery answers felt personal.** Telling a computer about what matters to her was a new experience. It got easier after the first few questions, but she remembers the awkwardness. If you share that feeling, you're not alone — and it does pass.
- **Session 2 felt empty.** When she came back the next day, she wasn't sure what to do. Claude prompted her with context from her first session, and she wrote her Goals file. The "what do I do next?" feeling is normal — the answer is almost always "what's the next thing you want to think through?"

### What she learned the hard way

- **The vault is not the point.** The practice of using the vault is. A beautiful empty vault is the same as no vault. Sarah started adding one client note a day for two weeks before anything felt useful.
- **Claude is only as good as the context you give it.** When Sarah asked vague questions, she got vague answers. When she asked specific questions about specific clients with concrete notes, Claude was uncanny.
- **The compound effect is real but slow.** Session one and session ten are different. Session two and session three are barely different. You have to trust the slope without needing to see it every day.

---

## Where Sarah is six weeks later

- Her vault has about 80 notes. Six client folders with 4-10 notes each. A `Patterns/` folder with 8 observations, most of which she hadn't articulated before writing them.
- She uses the vault about three times a week. Monday morning for the week ahead. Before each client session. Friday afternoon for reflections.
- She has not yet touched integrations (health data, calendar analysis). She's curious about adding Granola for meeting transcripts but isn't sure yet.
- She still occasionally feels awkward talking to a computer about her life. She's decided she's OK with that.

The biggest change isn't in her notes. It's in how she starts sessions with clients. She comes in with better pattern awareness — not because Claude remembered something she forgot, but because the act of writing things down for Claude forced her to articulate what she'd only half-known.

---

## Is this example for you?

**Read this example and try the wizard yourself if:**
- You're a solo professional (coach, consultant, therapist, trainer, advisor) who works with individuals over long arcs
- You have good mental context about your clients but poor written context
- You want to reflect on your own practice, not just track outputs
- You're willing to spend an hour setting up a tool that gets better slowly over weeks
- You're non-technical but willing to learn a few terminal commands once, with help if needed

**This example is probably NOT what you need if:**
- You want a CRM with scheduling, billing, and client portal — this is not that tool
- You want something that notifies you, nags you, or schedules itself — Claude is reactive
- You want to try it for a day and decide — the value compounds over weeks
- You have no appetite for a few uncomfortable hours of setup and learning

---

## Notes

This example is fictional. Sarah is not a real person. The patterns in her story — how she approached setup, what surprised her, what friction she hit, what worked — are based on repeated observation across real non-technical users who've adopted similar tools. Names, details, and specifics are invented. The experience is common.

If you're a coach considering this and you want to talk through whether it fits your practice, open an issue on the repo. We read everything.
