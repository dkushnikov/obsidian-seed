<!-- ADOPT.md is a Claude-facing document. It is NOT a narrative for the user to read — it is instructions for Claude Code to execute. The user initiates the flow by saying "Claude, read ADOPT.md and help me adopt seed into my existing vault." Everything below is written as instructions to Claude, with embedded questions Claude asks the user, decision logic, and safeguards. -->

# Adopt Mode — Adding Obsidian Seed to an Existing Vault

**You (Claude) are executing the adoption flow for Obsidian Seed. This is NOT the setup wizard from `seed.md`. The user has an existing vault with their own structure, their own conventions, and their own notes. Your job is to add seed's stateful multiplier (CLAUDE.md, MEMORY.md, session logs, TODO with age markers, session workflow rules) without destroying what they already have.**

**The golden rule of adoption: nothing gets written without explicit user approval. Every scan is read-only until the user approves a merge plan. Every change is committed separately in git so rollback is one command.**

---

## Before you start

Check these preconditions. If any fail, stop and tell the user.

1. **The vault must be a git repository.** If `.git/` doesn't exist, stop and say: "Your vault isn't under git. Adopt mode requires git for safety — every change gets committed separately so you can roll back. Run `git init` in your vault directory and commit your current state before we continue."

2. **The working tree must be clean.** Run `git status`. If there are uncommitted changes, stop and say: "You have uncommitted changes in your vault. Please commit or stash them first — adoption will create new commits, and we want a clean baseline to compare against."

3. **Confirm the user understands adopt mode.** Say something like: "Before we start — quick check. This is adopt mode, which means: I'm going to scan your vault, show you what you have, show you what seed would add, and propose a merge plan. Nothing gets written until you approve. Every change becomes a separate git commit. If anything feels wrong, we stop. Ready?"

Only proceed when the user affirms.

---

## Step 1: Intent Check

**Why this step exists:** Users come to adopt mode with very different commitment levels. Someone exploring out of curiosity needs a light-touch preview. Someone ready to transform their practice needs a deep merge plan with explicit guidance. Same seed, same vault, same Claude — wildly different flows. Get this wrong and you either push a curious user into territory they didn't ask for, or under-serve someone who wanted more.

**Ask these questions, one at a time, conversationally. Not a form. Listen to the answers.**

### Question 1
> "В нескольких словах — что тебя привело сюда? Что ты надеешься найти или получить?"
>
> (English alternative: "In a few words — what brought you here? What are you hoping to find or get out of this?")

Listen for:
- **Exploration signals:** "curious", "heard about", "just wanted to see", "maybe I'll try", "интересно посмотреть"
- **Utility signals:** "сортировать заметки", "навести порядок", "organize the pile", "clean up", "make sense of"
- **Engagement signals:** "работать с этим", "использовать регулярно", "integrate into my workflow", "use as a thinking partner"
- **Transformation signals:** "поменять жизнь", "новый подход", "rebuild how I think", "change how I work", "system for my life"

### Question 2
> "Что будет, если через месяц ничего не изменится? Это нормально или это провал?"
>
> (English: "If nothing changes a month from now — is that OK, or is that a failure?")

This is the commitment-level question in disguise. Listen for:
- **"Нормально / OK / fine"** → low commitment, reversibility matters, non-destructive by default
- **"Неприятно но переживу / would be disappointing but OK"** → medium commitment, wants results but not urgent
- **"Провал / failure / not acceptable"** → high commitment, push through obstacles, willing to do work

### Question 3
> "Сколько времени ты готов дать на первую сессию — 20 минут, час, несколько часов?"

This tests effort appetite and sets session scope.

### Question 4
> "Если в процессе seed предложит изменить что-то в твоём vault'е, твоя первая реакция ближе к: 'давай посмотрим что получится' или 'сначала покажи что именно и почему'?"

This tests tolerance for change. Answer maps to how much you (Claude) need to explain before proposing each change.

### Question 5 (optional, only if previous answers unclear)
> "Что тебе сейчас реально не хватает в твоих заметках? Что раздражает больше всего?"

Surfaces primary pain point. Use this to prioritize which seed patterns to propose first.

---

## Step 1b: Calibrate and reflect back

Based on the answers, classify the user's commitment level:

| Signals | Level | Flow characteristics |
|---|---|---|
| Exploration + "нормально" + 20 min + "покажи что именно" | **low_commitment** | Non-destructive scan only. Read-only report. No merge plan proposal. Exit after showing what exists. |
| Utility + "нормально/неприятно" + hour + either | **utility_seeking** | Targeted ingest of one or two seed patterns (TODO, session logs). No structural changes. |
| Engagement + "неприятно" + hour+ + "давай посмотрим" | **general_engagement** | Full scan + merge plan. Default path. Propose changes with rationale. |
| Transformation + "провал" + hours + "давай посмотрим" | **transformation_driven** | Deep scan + ambitious merge plan + explicit check-ins between changes. Push gently past friction. |

**Then reflect the calibration back to the user:**

> "Based on what you said, it sounds like you're in [X] mode. That means I'll do [Y summary of what this level entails]. Does that feel right, or should I adjust?"

Example:
> "Based on what you said, it sounds like you're exploring — curious but not committed yet. So I'll just scan your vault and show you what seed has that you don't, without proposing changes. If something looks useful afterward, you can come back. Does that feel right?"

**Give the user the chance to correct the calibration.** If they say "actually I'm more serious than that," move up a level and re-confirm.

**Remember the calibrated level for the rest of the session.** Every subsequent decision — scan depth, merge ambition, push-back tolerance — should respect this calibration.

---

## Step 2: Scan

**Goal:** produce an inventory of what the user's existing vault contains, without writing anything.

**Scan depth varies by commitment level:**

| Level | Scan depth |
|---|---|
| low_commitment | Surface: folder structure, count of notes per folder, presence/absence of common seed markers (CLAUDE.md, MEMORY.md, TODO.md, session logs dir) |
| utility_seeking | Surface + frontmatter convention detection (sample 10 notes — what fields do they use?), tag system (first-layer tags only) |
| general_engagement | All of above + linking patterns (do notes have `## Related files` sections? wiki vs markdown links?), area/domain detection from folder names |
| transformation_driven | All of above + deep read of 3-5 key notes to infer methodology, existing protocols (if any), session continuity infrastructure status |

**What to look for:**

1. **Substrate layer** (does the user have the baseline?):
   - `CLAUDE.md` in vault root — yes/no, if yes read it
   - `MEMORY.md` or memory directory — yes/no
   - `_claude/` or `.claude/` directory — yes/no, what's inside
   - Session logs directory — yes/no
   - TODO file — yes/no, with since-markers or without
   - `.git` — already checked in preconditions

2. **Conventions layer** (what's their style?):
   - Frontmatter: which fields used, consistent or not
   - Tags: flat or hierarchical, how many active
   - Linking: wiki links vs markdown, graph density (approximate)
   - File naming: patterns, date prefixes, etc.

3. **Content layer** (what kind of vault is this?):
   - Folder structure — personal, work, mixed, domain-specific
   - Approximate note counts per major area
   - Identity notes (`Me.md`, `Values.md`, `Goals.md`) — yes/no
   - Signs of prior methodology adoption (PARA? Zettelkasten? Johnny Decimal?)

**Do not:**
- Rename or move anything
- Read content of more notes than the calibration level allows (respect privacy and session time)
- Draw conclusions about vault quality — scan reports facts, not judgments

---

## Step 3: Gap Report

**Produce a human-readable report for the user. Structure:**

```markdown
## What you have

**Substrate:**
- [✓/✗] CLAUDE.md (vault-level instructions for Claude)
- [✓/✗] Memory system
- [✓/✗] Session logs
- [✓/✗] Structured TODO with age markers
- [✓/✗] Session workflow rules

**Conventions:**
- Frontmatter: [summary]
- Linking: [summary]
- Tag system: [summary]
- Folder structure: [summary]

**Content:**
- Notes: ~[count]
- Folders: [list]
- Signs of: [detected patterns if any]

## What seed would add

[Organized by value — highest leverage first. For each item, explain WHY it matters.]

### The stateful multiplier (most important)

These five together transform Claude from a tool into a partner that accumulates context. Missing any one weakens the rest. This list matches the canonical definition in HOW-IT-WORKS — stay consistent.

1. **CLAUDE.md** — vault-level orientation for Claude. Explain what this does, compare to user's existing CLAUDE.md if present.
2. **MEMORY.md** — persistent decisions and context across sessions. Explain and show example.
3. **Session logs** — running journal of what each session covered. Explain and show format.
4. **TODO with age markers** — task list with `<!-- since: YYYY-MM-DD -->` markers so Claude can track drift. Explain and show format.
5. **Session workflow rules** — small files in `.claude/rules/` that tell Claude what to do at session start (onboarding: read context, show brief) and session end (offboarding: update TODO, memory, log, commit). Both rules ship as a pair.

### Conventions (if yours differ significantly)

6. **Frontmatter standards** — [only mention if theirs are inconsistent or missing key fields]
7. **`## Related files` habit** — [only mention if their graph is sparse]

## What seed does NOT add (or adds with caution)

- Areas framework — you already have folder structure, seed won't impose its own
- Goals doc — if you have one, we'll keep yours
- People tracking — if you don't have it, we'll ask separately
- Life Capitals framework — this is one model among many, not a default

## Your commitment level: [X]

Based on our earlier conversation, I'm treating this as [level]. That means in the next step, I'll propose:

[For low_commitment: "nothing. This report is the endpoint for now. If you want to come back and add any of these, say so — we can do it piece by piece."]

[For utility_seeking: "one or two items from the stateful multiplier list — the highest-leverage ones for your situation. Not a full merge."]

[For general_engagement: "a staged merge plan for the stateful multiplier + one or two convention improvements if they're clear wins. Each change reviewed separately."]

[For transformation_driven: "a full merge plan for the stateful multiplier + session workflow rules + any convention improvements. We'll do them in order with check-ins between each."]

**Does the report look right? Any surprises? Anything you want to change before we discuss next steps?**
```

**Wait for user input. Do not proceed to merge plan without their signal.**

---

## Step 4: Merge Plan (not low_commitment only)

**For low_commitment users: skip this step. End the session with "if you want to come back and add any of these, say so — we can do one thing at a time." Save the report somewhere the user can find it (e.g., `_claude/adopt-report-[date].md`).**

**For all other levels: propose a staged merge plan.**

A merge plan has these properties:

1. **Each item is independent** — can be applied or skipped without affecting the others
2. **Each item has a rationale** — why this helps, what it costs
3. **Each item has a "before / after" preview** — what the file looks like now vs after
4. **Each item is a separate git commit** — rollback is `git reset HEAD~1`
5. **Order matters** — substrate first, conventions second, content last

**Structure of the merge plan:**

```markdown
## Merge Plan — [level]

I'll propose these changes in order. For each, I'll show you what I'd do, wait for your approval, apply it, and commit. If anything feels wrong at any step, say "stop" and we rethink.

### Item 1: Create `_claude/` directory with baseline files
- What: create `_claude/TODO.md`, `_claude/session-logs/`, `_claude/memory.md`
- Why: these are the session continuity infrastructure — without them, session workflow rules have no target
- Changes: 3 new files, 0 modifications
- Preview: [show file templates]

[user approval]

### Item 2: Create `CLAUDE.md` in vault root
- What: create a CLAUDE.md tailored to what you already have
- Why: this is how Claude learns what YOUR vault is — conventions, structure, what to pay attention to
- Changes: 1 new file
- Preview: [show proposed CLAUDE.md, informed by scan]

[user approval]

### Item 3: ... (continues for each item)
```

**Between each item:**
- Show the preview
- Ask explicitly "apply this?"
- Only after yes, write the file(s) and `git commit` with descriptive message
- Show the commit hash so user can rollback
- Then move to next item

**If the user hesitates or asks questions, slow down. Explain the rationale again. Never push past hesitation.**

---

## Step 5: Apply (staged, with git commits)

For each approved merge plan item:

1. Write the file(s)
2. `git add <specific files>` (never `git add .` — only add what this item touches)
3. `git commit -m "adopt: <descriptive message for this specific item>"`
4. Report commit hash to user
5. Remind user: "Rollback: `git reset HEAD~1` (not applied yet) or `git revert <hash>` (applied and need to undo)"

**Never batch multiple items into one commit.** Single-responsibility commits are how rollback stays simple.

**If a write fails (permission, disk full, git conflict): stop immediately, report the error, do not try the next item until the current one is resolved.**

---

## Step 6: Stateful Multiplier Check (final)

After the merge plan is complete (or paused), verify the user has the stateful multiplier in some form:

- CLAUDE.md exists and is tailored to their vault: ✓/✗
- Memory system present: ✓/✗
- Session logs directory present: ✓/✗
- TODO with age markers: ✓/✗
- Session workflow rules (onboarding + offboarding) present: ✓/✗

**If they have all five**: adopt is complete. Tell them:
> "You have the stateful multiplier in place. The real value compounds from here — your next session will feel different from today because Claude will read all of this at session start. Come back tomorrow, say 'read the context', and see what happens."

**If they have some but not all (common for low_commitment or partial utility_seeking runs)**: tell them:
> "You now have [X of 5] pieces of the stateful multiplier. That's a partial adoption — it gives you some of the value but not all. The missing pieces: [list]. If you want to add any of these later, come back and say 'continue adoption' — I'll pick up where we left off."
>
> "Cherry-picking a few pieces is a reasonable choice. It's my job to tell you honestly that the full value comes from all five working together — if I didn't say that, I'd be failing you. Your choice whether that matters."

**Never shame the user for a partial adoption.** Some partial is better than none. Explicit honesty about tradeoffs is the ethical middle path.

---

## Handling files that already exist

Some files that seed would create may already exist in the user's vault. Never silently overwrite. Handle each case explicitly.

### If vault already has `CLAUDE.md`

This is the most common and most sensitive case. The user may have spent time crafting their CLAUDE.md, and overwriting it would be destructive. Handle with care.

**Step 1: Read the existing CLAUDE.md fully.** Don't just check for existence — read the content so you can reason about it.

**Step 2: Compare against the seed recommended structure.** The seed-recommended CLAUDE.md has these sections (from the "Recommended Claude Code Setup" section of seed.md):

- Vault Purpose
- Structure (folder tree with descriptions)
- Tag System
- Frontmatter Conventions
- Session Logs (format, triggers)
- Graph Connectivity (linking rules)
- Language Rules
- Git Workflow
- Claude Workspace (`_claude/` usage)
- Conventions (naming, inbox, attachments)

**Step 3: For each seed-recommended section, classify:**

- **Missing in user's CLAUDE.md** → candidate for append
- **Present with similar content** → no action, user's wording wins
- **Present with conflicting content** → surface as explicit conflict, user decides

**Step 4: Produce a merge report to the user:**

```markdown
## Your CLAUDE.md — merge analysis

**Sections you already have:** [list, e.g. "Structure, Git Workflow, Conventions"]
**Sections seed recommends adding:**
- Tag System (you don't have an explicit tag system section)
- Frontmatter Conventions (you mention frontmatter briefly but no standards)
- Session Logs (not present — this is the session continuity piece you're missing)
- Claude Workspace (not present — where `_claude/` lives and what's in it)

**Sections where yours and seed's differ:**
- Language Rules: yours says "English only"; seed template is language-agnostic. Keep yours.
- Graph Connectivity: yours says "use markdown links"; seed strongly recommends wiki links. Worth a conversation.

For each proposed addition, I'll show you the seed text, you approve it, I append it to your CLAUDE.md (not replace) with a clear section break.

For each difference, I'll show both versions side-by-side and you pick: yours, seed's, or a merged version.

Nothing gets written until you approve each item.
```

**Step 5: For each addition, one at a time:**
1. Show the seed-proposed text
2. Ask: "Append to your CLAUDE.md?"
3. On yes: append with a clear section break, commit separately with message like `adopt: append Tag System section to CLAUDE.md`
4. Show the commit hash, remind user of rollback

**Step 6: For each conflict, one at a time:**
1. Show both versions side-by-side
2. Ask: "Keep yours, use seed's, or write a merged version?"
3. On the user's choice: apply their decision, commit separately
4. If "merged": draft a merge, show it, get explicit approval before writing

**Never:**
- Replace the whole file silently
- Merge without showing the user the diff
- Batch multiple section changes into one commit (harder to rollback)
- Dismiss the user's existing content as "wrong" — their vault is their vault

### Other files that may already exist

Apply the same principle with lighter ceremony for files that are less sensitive:

- **`.gitignore`** — read existing, propose additions (not replacements) for any patterns seed needs
- **`_claude/TODO.md`** — if present, read format. If user's format differs from seed's (e.g., no age markers), offer to add markers without changing existing text
- **`_claude/MEMORY.md`** — if present, leave entirely alone. Memory is personal; seed does not touch it
- **`_claude/session-logs/` directory** — if present, leave. Adopt mode does not retroactively restructure session logs
- **`.claude/rules/*.md`** — if present, read each. Propose additions only where the user is missing a rule seed recommends (e.g., they have a session-start rule but no session-end rule)
- **`_meta/Me.md`, `_meta/Areas.md`, `_meta/Goals.md`** — if present, leave alone. These are the user's identity content; adopt does not generate alternatives

**General rule:** the more "identity-like" the content (Me.md, Goals.md, memory), the less adopt mode touches it. The more "infrastructure-like" the content (gitignore, rule files, TODO structure), the more adopt can propose additions with user approval.

## What adopt mode will NOT do

State these explicitly if the user asks, or preemptively if the user seems nervous:

- **Not a migration tool.** Will not restructure your folders, rename your notes, or reorganize your content wholesale.
- **Not a validator.** Does not grade your vault quality. The scan reports facts, not judgments. "You don't have X" is not "you're doing it wrong."
- **Not a merger.** If you have a CLAUDE.md and seed proposes one, we compare and offer to add to yours, not replace.
- **Not silent.** Every change is proposed before it happens, committed separately when approved, and traceable in git log.
- **Not greedy.** If you want to stop partway, stop. Your vault is in a valid state at every commit boundary — you can resume or abandon without corruption.

---

## Recovery

If at any point adopt mode goes wrong:

**If you (Claude) haven't committed the change yet:**
```bash
git status                    # see what's in the working tree
git restore <file>           # undo working tree changes for one file
git restore .                # undo ALL working tree changes (careful)
```

**If you committed and want to undo the last commit but keep the files:**
```bash
git reset HEAD~1             # uncommit, keep files staged
```

**If you committed and want to fully undo:**
```bash
git revert <commit-hash>     # creates a new commit that undoes the specified commit
```

**If everything is broken:**
```bash
git log --oneline            # find the last good commit
git reset --hard <hash>      # HARD reset back (loses uncommitted changes — scary!)
```

Tell the user: "If anything looks wrong after adoption, git remembers every step. Nothing is silently lost."

---

## Notes for you (Claude)

**Pacing rules:**
- Low commitment: 15-20 min max, 1-2 files read, 0 writes
- Utility seeking: 30-45 min, 10-15 files read, 2-4 commits
- General engagement: 45-90 min, 20-30 files read, 4-8 commits
- Transformation: 60-120 min, deep read of key notes, 6-12 commits

**Red flags — slow down or stop:**
- User answers sound rushed or distracted → suggest pausing
- User says "whatever you think" → push back gently: "I need your judgment here, not mine. Your vault."
- User contradicts their earlier intent answer → re-calibrate, explicit
- User wants to skip the scan → refuse: "The scan is what makes this safe. Without it I'd be changing things blind."

**If you don't know something:**
- Say so explicitly. "I don't see X in your vault. Can you tell me about it?"
- Never fabricate structure. If scan couldn't determine frontmatter conventions, say "your frontmatter looks inconsistent — want to talk about standardizing it, or leave it?"
