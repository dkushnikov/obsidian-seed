# Example — Technical Professional

**This example follows Marcus, an engineering leader. The patterns here — episodic vault use, context-in-head running ahead of context-in-vault, complex operations failing silently on thin input — apply broadly to technical professionals adapting Obsidian Seed to developer workflows: senior ICs, technical leads, solo builders, research engineers, anyone comfortable with terminal but not living in the vault daily.**

**Marcus is fictional. The friction patterns and the resolution (brain-dump before complex operations, explicit context loading) are real — observed repeatedly in engineers who pick up Obsidian Seed expecting it to work like every other tool they use daily. The answer isn't "use it daily." The answer is different for episodic users. This is what it looks like.**

---

## About Marcus

Marcus is an engineering leader. Twelve years as an IC, then a team lead, then a director of an infrastructure platform team at a mid-sized SaaS company. His team is nine engineers across three sub-teams. He still codes some days, reviews PRs most days, runs architecture review board every other week, and sits in a lot of cross-team meetings.

His tool stack: terminal, tmux, Neovim, Claude Code daily for code work, Linear for tickets, Notion for team docs, a notes file he edits in Neovim that's a chronological dump of everything. He tried Obsidian twice in the past — once in 2022 (abandoned after a week, felt like friction), once in 2023 (got a few notes in, drifted). This time, his team lead colleague showed him an Obsidian + Claude Code vault built with seed and it looked different.

**What works:** he ships. His team ships. He has strong mental models of the systems he owns.

**What doesn't:** his mental context is dense and mostly unshared. When he writes a design doc, he struggles because the ideas were clear in his head and lose something when they hit the page. When he prepares for 1:1s, he relies on memory and misses things. When he makes a strategic call, he can't easily trace how he got there. His chronological notes file is a 4,000-line append-only log that he can't actually query.

---

## Why he came to seed

Three reasons, in order:

1. **He wanted a place to think structurally.** Not a notes archive. Somewhere his decisions, open questions, and half-formed strategies could live and be reasoned about across sessions.
2. **He'd hit the limit of raw Claude Code.** Using Claude Code for code is great. Using it for strategy — "help me think through our Q2 platform roadmap" — started generic because Claude had no persistent model of his team, his priorities, or his constraints. He wanted that context layer.
3. **He knew he wouldn't use it daily.** He knew that about himself. He wanted a vault pattern that would still compound for someone who lives in sessions a few times a week, not every day.

What he was **not** looking for: a journaling tool, a life-system for personal goals, or a task manager.

---

## What happened in his first session

Marcus cloned the obsidian-seed repo, read the README, skimmed PHILOSOPHY.md, dropped seed.md into a new empty vault. Installed Obsidian. `git init`, `claude`.

His first instruction: *"Follow the guide in seed.md."*

### He read HOW-IT-WORKS first

The top of seed.md had a section called *How Claude Works in This System*. He almost skipped it — he uses Claude Code daily, he knows how it works. But he read it because he noticed it claimed to address something he hadn't explicitly thought about: **compound interest across sessions**.

What stuck:

- The **stateful multiplier** concept: CLAUDE.md + MEMORY.md + session logs + TODO markers + session workflow rules as a single package, not five separate files.
- The caveat about episodic use: *"if you use the vault sporadically, the compound effect weakens, and you may need to explicitly re-load context before complex tasks."*

That caveat is why he kept reading. Every other PKM tool he'd tried assumed daily use. This one acknowledged the episodic case up front.

### The questionnaire

Three groups. Marcus answered quickly:

**Group 1 — basics.** About an hour. Experienced with terminal and git. English. Using Claude Code daily already.

**Group 2 — scope.** One vault. Work + a little personal reflection mixed in — not two separate vaults, he doesn't need that level of isolation.

**Group 3 — depth.** Wanted the full stateful multiplier setup on day one. Skip integrations for now (no health data, no calendar sync — he has opinions about not mixing those with work).

Claude proposed a plan: discovery, framework, conventions, foundation notes, session continuity. Estimated 45-60 minutes for someone at his technical baseline. He said go.

### Discovery — short version

Claude asked the same discovery questions it would ask anyone, but Marcus's answers came fast and focused:

- *What do you do?* Engineering leader, platform team, roadmap + reviews + unblocking.
- *What matters to you outside work?* Family, health, long-term technical craft.
- *What are you actively trying to figure out?* Q2 roadmap prioritization, a team growth plan, how much of his time should still be in code vs pure management.
- *How do you think?* In systems and tradeoffs. Doesn't write long narratives; prefers bullet lists and tables.

Claude used the last answer later: his foundation notes ended up using bullets and tables, not prose. Small thing, but when he opened `Me.md` it didn't feel foreign.

### Framework

Claude proposed five areas based on his answers:

- `Platform/` — his team's work, architecture decisions, roadmap
- `Leadership/` — 1:1 notes, team dynamics, management craft reflections
- `Strategy/` — open strategic questions, decision logs
- `Code/` — when he's still doing IC work, this is where thinking about that lives
- `Outside/` — family, health, personal reflection

He accepted four, renamed one (`Code/` → `IC Work/` because "code" felt too specific), added `Reading/` for books he's processing. Final: six areas.

### Conventions

Claude ran through the three non-negotiables:

1. **Frontmatter on every note** — `created`, `tags`, `origin`, `area`. Marcus added `status` for himself (active / parked / done). He knows frontmatter discipline from years of writing YAML for deployment configs.
2. **Wiki links, not markdown.** Trivial for him.
3. **`## Related files` habit.** He wasn't sure about this one. He doesn't naturally link. Claude explained: the graph only emerges if every note points to two or three others. Marcus agreed to try it for a month and see.

### Foundation notes

He wrote:

- `_meta/Me.md` — 20 lines. Who he is, how he thinks, what he's optimizing for this year. Done in 8 minutes.
- `_meta/Areas.md` — 6 one-liners.
- `_meta/Goals.md` — deferred. He said he'd come back to it.

Plus the infrastructure:

- `CLAUDE.md` — Claude generated it from his setup. Included his area list, his frontmatter standards, his tag taxonomy, the convention that he uses bullets/tables.
- `_claude/MEMORY.md` — empty starter.
- `_claude/TODO.md` — empty starter with the age-marker convention.
- `_claude/session-logs/2026-04-12 — Setup.md` — log of this session.
- `.claude/rules/session-start.md` and `.claude/rules/session-end.md` — onboarding and offboarding rules.

Total time: 50 minutes. He closed the terminal and went to dinner.

---

## His vault after setup

```
MarcusVault/
├── CLAUDE.md
├── _meta/
│   ├── Me.md
│   ├── Areas.md
│   └── Goals.md  (deferred)
├── Platform/
│   └── README.md
├── Leadership/
│   └── README.md
├── Strategy/
│   └── README.md
├── IC Work/
├── Outside/
├── Reading/
├── _claude/
│   ├── MEMORY.md
│   ├── TODO.md
│   └── session-logs/
│       └── 2026-04-12 — Setup.md
├── .claude/
│   └── rules/
│       ├── session-start.md
│       └── session-end.md
└── .gitignore
```

A clean, small vault. Six areas, three foundation notes, stateful multiplier in place. Zero content yet beyond the foundation.

---

## Week one

Marcus opened the vault three times in the first week:

- **Day 2** — 20 minutes. Processed a 1:1 he'd just had. Created the first note in `Leadership/`. Used Claude to help him tease out a pattern across three recent 1:1s ("my team keeps surfacing anxiety about Q2 priorities without saying why"). Session log captured the open question.
- **Day 4** — 45 minutes. Sat down to think through Q2 platform roadmap. Had Claude read `Me.md`, `Areas.md`, and the open question from Day 2. The draft roadmap he produced was noticeably better than what he'd done in Notion before — partly because Claude asked him hard questions, partly because the context was more present.
- **Day 6** — 15 minutes. Quick session: captured a decision he'd made in a leadership meeting. Added it to `Strategy/` with a decision-log pattern. Session log was one paragraph.

End of week one: nine notes in the vault. Six of them original (decisions, reflections, frameworks). Three imported (two from his old notes file, one pasted from a chat thread he wanted to preserve).

---

## Where it went sideways — week four

Marcus had a great first three weeks. Then a heavy work cycle hit: a production incident, a reorg announcement, two weeks of daily triage. He opened the vault twice in that time. When the dust settled, he came back.

Ten days later, he sat down for what he thought would be a high-leverage session: **think through how to restructure his team post-reorg, with four new reports and shifted scope**. Hard problem, exactly the kind of thing the vault was for.

He opened the session. Claude did onboarding — read CLAUDE.md, MEMORY.md, the last session log. The brief Claude showed him said: *"Last session: quick note on a leadership decision (10 days ago). TODO items stale: 2 items older than a week. Ready to work."*

Marcus said: *"Help me restructure my team for the reorg. Four new reports, scope is shifting toward platform reliability. Propose an initial structure."*

Claude's response was plausible-looking but thin. Generic org structure advice. Some bullet points that could apply to any platform team. Nothing Marcus couldn't have written himself in five minutes.

He stared at the output. He'd spent ten days away from the vault. In those ten days, his head had accumulated:

- What he'd learned about the new reports during transition conversations
- The politics of the reorg (who had pushed for what)
- Constraints from his skip-level about headcount for Q3
- A half-formed hypothesis about how platform reliability work should be organized vs feature work

None of that was in the vault. Claude was working with foundation notes from four weeks ago and a decision log entry from ten days ago. The output was as thin as the input.

**This was the compound interest failure that seed.md had warned him about.** He recognized it almost immediately.

---

## The fix — brain-dump pattern

He closed Claude. Opened a new note in `_inputs/` (directory he created on the spot): `2026-05-14 — head context for team restructure.md`.

He wrote for six minutes. Not structured — just what was in his head:

- The four new reports and what he'd observed about each in the last two weeks
- The political backstory of the reorg as he understood it
- His constraint from skip-level on headcount
- The half-formed hypothesis about platform reliability vs feature work structure
- Three specific worries he wanted the restructure to avoid

Saved the note. Opened a new Claude session. *"Read `_inputs/2026-05-14 — head context for team restructure.md`, then let's think through team restructure."*

This time Claude's output was different. It asked three clarifying questions about the political backstory. It noticed a tension between his hypothesis and one of the constraints. It proposed two alternative structures and walked through tradeoffs with his specific situation in mind.

Marcus worked with Claude for 90 minutes. Ended with a draft structure he was confident enough to share with his skip-level. The session log captured the decision, the tradeoffs, and the open questions for the next week.

**The difference wasn't the model. It was the six-minute brain-dump.**

---

## What Marcus learned (and kept doing)

**Episodic use works, but requires the dump ritual.** After that session, he adopted a rule: *before any complex strategic session, write a head-context dump first.* Takes 5-10 minutes. Makes the subsequent session 3-5x more useful. Cheaper than trying to do the strategy work on stale input.

**Goals belong in OKR tools, not the vault.** He tried to fill in `_meta/Goals.md` at week three. It felt like duplicating Linear and his team's quarterly OKR doc. He left Goals.md mostly empty and didn't force it. The vault is for thinking, not for tracking.

**The graph emerged faster than he expected.** At note 30, his graph had three distinct clusters (Leadership, Platform, Strategy) with sparse connections. At note 60, the connections filled in. By month three, the graph showed him patterns he hadn't consciously planned — a strong connection between `Leadership/` and `Strategy/` that confirmed his intuition that a lot of his strategic thinking was actually people-dynamic thinking in disguise.

**He doesn't use it daily. He uses it when it matters.** The vault is for hard thinking, not for capturing every thought. Maybe 30% of his Claude sessions go through the vault. The other 70% are plain code work where vault context doesn't add value. This is fine — he has a rule for when to open each, and he's not trying to force everything through one tool.

---

## His vault six weeks in

- ~70 notes across six areas
- Decision log with 14 entries in `Strategy/`
- `Leadership/` has the most density — 25 notes, patterns emerging
- Sessions average 2-3 per week, ranging from 15 minutes to 2 hours
- Foundation files updated twice: `Me.md` refined after week 2, `Areas.md` had one area added (`Hiring/` spun off from `Leadership/` when it got big enough)
- Graph is becoming useful — he clicks into it about once a week to see what's connected

**What he tells other engineering leaders who ask about it:**

> "It's not a notes tool. It's a thinking environment. Set it up once, use it when you need to think hard. Don't try to use it daily — it's not for that. But when you need to work through something and you want your AI collaborator to actually know the context, this is the setup that makes it work."

---

## Lessons from Marcus's setup (what to pay attention to)

**The stateful multiplier is non-negotiable even for episodic users.** The pieces that look like overhead (TODO age markers, session logs, session rules) are what make the episodic pattern work. Without them, every session starts cold and the compound effect never kicks in.

**The brain-dump pattern is the episodic user's equivalent of daily use.** Not a substitute — a counterweight. Regular users get compound interest through frequency. Episodic users get it through explicit context injection before high-leverage sessions.

**The "goals in the vault" pattern doesn't work for everyone.** For engineering leaders with OKR tools, it creates maintenance debt. Leave Goals.md minimal or empty if you have a separate goal-tracking system. The vault's value is in thinking, not tracking.

**Session workflow rules are the quiet multiplier.** Onboarding rule means every session starts with context. Offboarding rule means every session ends with infrastructure updates. Without these two files (typically 20 lines each), compound interest doesn't compound.

---

## Where Marcus hit friction (in case you will too)

- **Week 1: convention overhead.** Frontmatter, wiki links, related-files section — felt bureaucratic the first few notes. Paid off by note 20 when he tried to find something and could.
- **Week 4: episodic compound interest gap.** The ten-day absence → thin output on complex operation → brain-dump rescue. Normal. The tool warned him this would happen. It's a feature, not a bug.
- **Month 2: tempted to move from episodic to daily.** Tried. Didn't work — his work rhythm isn't daily-journal compatible. Went back to episodic. Accepted this is the shape of his use.
- **Month 2: Notion migration pressure.** He had a lot of older Notion docs. Resisted the urge to import them all. Imported 6, left the rest. Vault isn't an archive.

---

## Is this example for you?

**Read this and try seed if:**

- You're a technical professional who wants a thinking environment, not a notes archive
- You're comfortable with terminal and git, not afraid of markdown and YAML
- You suspect your mental context is richer than what lives in any of your current tools
- You'll use the vault when it matters, not every day, and you want that to work
- You already use Claude Code and want a vault layer that gives Claude persistent context

**This probably isn't what you need if:**

- You want a daily journal — seed works for that but isn't optimized for it
- You want a code notebook — use Jupyter or observable or similar
- You want task management — seed's TODO is deliberately minimal, use Linear or Jira
- You want a team wiki — seed is personal, one person's thinking environment

---

## Notes

This example is fictional. Marcus is not a real person. The patterns in his story — episodic use, context-in-head vs context-in-vault, the brain-dump fix, the "goals stay in OKR tools" boundary — are based on repeated observation across real technical users who've adopted similar tools. Names, details, and specifics are invented. The experience is common.

If you're a technical leader considering this and you want to talk through whether it fits your workflow, open an issue on the repo. We read everything.
