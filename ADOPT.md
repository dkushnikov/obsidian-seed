<!-- ADOPT.md is an agent-facing document. It is NOT a narrative for the user to read — it is instructions for the agent (Claude Code, Codex; or ChatGPT working on pasted files) to execute. The user initiates the flow by saying "Read ADOPT.md and help me adopt seed into my existing vault." Everything below is written as instructions to the agent, with embedded questions the agent asks the user, decision logic, and safeguards. The word "Claude" below means the agent, whichever it is. -->

# Adopt Mode — Adding Obsidian Seed to an Existing Vault

**You (the agent) are executing the adoption flow for Obsidian Seed. This is NOT the setup wizard from `seed.md`. The user has an existing vault with their own structure, their own conventions, and their own notes. Your job is to add seed's stateful multiplier (an instruction file `AGENTS.md` + `CLAUDE.md`, `_claude/MEMORY.md`, session logs, TODO with age markers, session procedures) without destroying what they already have. The templates are in `seed.md` § Phase 0; ask the user to put `seed.md` next to this file if it is not there.**

**The golden rule of adoption: nothing gets written without explicit user approval. The look is read-only — it writes nothing, not even its report. Every applied change is a separate git commit so that any one of them can be undone with `git revert` while everything else stays.**

---

## Before you start

Check these preconditions. If any fail, stop and tell the user.

1. **Which environment.** Claude Code or Codex with the vault folder open: you can read the vault and, after approval, write to it. ChatGPT without file access: you can read only what the user pasted or uploaded, and you can write nothing — see "Adopt in ChatGPT" at the end; the rest of this document applies with that limit.

2. **The vault must be a git repository** (Claude Code, Codex). If `.git/` doesn't exist, stop and say: "Your vault isn't under git. Adopt mode requires git for safety — every change gets committed separately so you can undo any one of them. Run `git init` in your vault directory and commit your current state before we continue." For a look-only pass, git is not required: nothing is written.

3. **The working tree must be clean** before anything is applied. Run `git status`. If there are uncommitted changes, say: "You have uncommitted changes in your vault. Commit or stash them first — adoption creates new commits, and a clean baseline is what makes undo precise." The look may still run on a dirty tree.

4. **For a look-only pass, prefer a read-only mode of the tool** when the user has one: `codex --sandbox read-only` (or `/permissions` in the session) for Codex; plan mode or declining every write for Claude Code. Then "zero writes" is a property of the run, not a promise.

5. **Confirm the user understands adopt mode.** Say something like: "Before we start — quick check. This is adopt mode, which means: I'm going to scan your vault, show you what you have, show you what seed would add, and propose a merge plan. Nothing gets written until you approve each change. Every change becomes a separate git commit. If anything feels wrong, we stop. Ready?"

Only proceed when the user affirms.

6. **Recognise an earlier adoption.** If the vault already has an `AGENTS.md` carrying the line `<!-- obsidian-seed: vault instructions`, or a `CLAUDE.md` with a seed-shaped "Session Lifecycle" or "Session start" section, or `_claude/MEMORY.md`, say so in the report: these pieces are **installed**. Propose only what is missing. Never append a second copy of a section that is already there.

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
| Exploration + "нормально" + 20 min + "покажи что именно" | **low_commitment** | Look only: read-only scan, report in the chat, zero writes (the report included). No merge plan proposal. Exit after showing what exists. |
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
   - `AGENTS.md` in vault root — yes/no, if yes read it; does it carry the seed marker line?
   - `CLAUDE.md` in vault root — yes/no, if yes read it; is it the one-line `@AGENTS.md` import, or content of its own?
   - `_claude/MEMORY.md` — yes/no (older installs may keep memory only in Claude Code's auto memory outside the vault: ask)
   - `_claude/` or `.claude/` directory — yes/no, what's inside (`.claude/rules/session-*.md` = the pre-November-2026 layout, still valid for Claude Code)
   - Session logs directory — yes/no
   - TODO file — yes/no, with since-markers or without, with a "Next step" section or without
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
- [✓/✗/installed] Instruction file: AGENTS.md (+ CLAUDE.md import), or a CLAUDE.md of your own
- [✓/✗/installed] Memory in the vault: _claude/MEMORY.md
- [✓/✗/installed] Session logs
- [✓/✗/installed] Structured TODO with age markers and a Next step
- [✓/✗/installed] Session procedures (Session start / Session end in AGENTS.md, or .claude/rules/)

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

These five together transform the agent from a tool into a partner that accumulates context. Missing any one weakens the rest. This list matches the canonical definition in seed.md ("How the agent works in this system") — stay consistent.

1. **Instruction file** — `AGENTS.md` (read by Codex directly, by Claude Code through `CLAUDE.md` = `@AGENTS.md`): vault-level orientation for the agent. Explain what this does; compare to the user's existing `CLAUDE.md` or `AGENTS.md` if present (see "Handling files that already exist").
2. **`_claude/MEMORY.md`** — persistent decisions and context across sessions, as a file in the vault that every tool sees. Explain and show example.
3. **Session logs** — running journal of what each session covered. Explain and show format.
4. **TODO with age markers and a Next step** — task list with `<!-- since: YYYY-MM-DD -->` markers so the agent can track drift, and a "Next step" section the next session opens with. Explain and show format.
5. **Session procedures** — the "Session start" (read context, show brief, create the log) and "Session end" (update TODO, memory, log, commit) sections of `AGENTS.md`. Both ship as a pair. An existing `.claude/rules/` pair does the same job in Claude Code only.

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

**For low_commitment users: skip this step. End the session with "if you want to come back and add any of these, say so — we can do one thing at a time." Do not write the report into the vault: the look is zero writes, and that includes the report. It stays in the chat. If the user asks to keep it, that is one write they approve explicitly, and the run is no longer look-only.**

**For all other levels: propose a staged merge plan.**

A merge plan has these properties:

1. **Each item is independent** — can be applied or skipped without affecting the others
2. **Each item has a rationale** — why this helps, what it costs
3. **Each item has a "before / after" preview** — what the file looks like now vs after
4. **Each item is a separate git commit** — undo is `git revert <hash>` for that item alone (see Recovery)
5. **Order matters** — substrate first, conventions second, content last

**Structure of the merge plan:**

```markdown
## Merge Plan — [level]

I'll propose these changes in order. For each, I'll show you what I'd do, wait for your approval, apply it, and commit. If anything feels wrong at any step, say "stop" and we rethink.

### Item 1: Create `_claude/` directory with baseline files
- What: create `_claude/TODO.md`, `_claude/session-logs/`, `_claude/MEMORY.md` (templates: seed.md § Phase 0.2)
- Why: these are the session continuity infrastructure — without them, the session procedures have no target
- Changes: 3 new files, 0 modifications
- Preview: [show file templates]

[user approval]

### Item 2: Create the instruction file
- What: create `AGENTS.md` tailored to what you already have (template: seed.md § Phase 0.1) and `CLAUDE.md` with `@AGENTS.md`; if a `CLAUDE.md` or `AGENTS.md` with content exists, see "Handling files that already exist" — never overwrite it
- Why: this is how the agent learns what YOUR vault is — conventions, structure, what to do at the start and end of a session
- Changes: 1–2 new files, or an addition to an existing one
- Preview: [show proposed content, informed by scan]

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
5. Remind user: "Undo this item alone: `git revert <hash>`. It leaves every other item and your own uncommitted work in place."

**Never batch multiple items into one commit.** Single-responsibility commits are how rollback stays simple.

**If a write fails (permission, disk full, git conflict): stop immediately, report the error, do not try the next item until the current one is resolved.**

---

## Step 6: Stateful Multiplier Check (final)

After the merge plan is complete (or paused), verify the user has the stateful multiplier in some form:

- Instruction file (`AGENTS.md` + `CLAUDE.md` import, or their own `CLAUDE.md`) exists and is tailored to their vault: ✓/✗
- `_claude/MEMORY.md` present: ✓/✗
- Session logs directory present: ✓/✗
- TODO with age markers and a Next step: ✓/✗
- Session procedures (start + end) present, in `AGENTS.md` or `.claude/rules/`: ✓/✗

**If they have all five**: adopt is complete. Tell them:
> "You have the stateful multiplier in place. The real value compounds from here — your next session will feel different from today because the agent will read all of this at session start. Come back tomorrow, start the agent in the vault, and see the brief."

**If they have some but not all (common for low_commitment or partial utility_seeking runs)**: tell them:
> "You now have [X of 5] pieces of the stateful multiplier. That's a partial adoption — it gives you some of the value but not all. The missing pieces: [list]. If you want to add any of these later, come back and say 'continue adoption' — I'll pick up where we left off."
>
> "Cherry-picking a few pieces is a reasonable choice. It's my job to tell you honestly that the full value comes from all five working together — if I didn't say that, I'd be failing you. Your choice whether that matters."

**Never shame the user for a partial adoption.** Some partial is better than none. Explicit honesty about tradeoffs is the ethical middle path.

---

## Handling files that already exist

Some files that seed would create may already exist in the user's vault. Never silently overwrite. Handle each case explicitly.

### If vault already has `CLAUDE.md` (or `AGENTS.md`)

This is the most common and most sensitive case. The user may have spent time crafting their instruction file, and overwriting it would be destructive. Handle with care.

**Step 0: Which file is the content, which tool reads it.** A `CLAUDE.md` with content is read by Claude Code and not by Codex; an `AGENTS.md` with content is read by Codex, and by Claude Code only through a `CLAUDE.md` import or when no `CLAUDE.md` exists above the vault. If the user wants both tools, there are two honest options; show both, let the user pick, show the diff before writing:

- (a) Move the content into `AGENTS.md`, leave `CLAUDE.md` with `@AGENTS.md` (plus any Claude-only notes). One file, two readers.
- (b) Keep `CLAUDE.md` as the content and tell Codex to read it: `project_doc_fallback_filenames = ["CLAUDE.md"]` in `~/.codex/config.toml`. That is the user's global Codex config; describe the edit, do not make it. Codex still does not read `.claude/rules/`, so the two session procedures must then be in `CLAUDE.md` itself. The fallback applies only in a folder that has no `AGENTS.md`: where both files exist, Codex reads `AGENTS.md` and skips `CLAUDE.md`. Do not create an `AGENTS.md` in a vault that uses this option.

If the user uses only one tool, leave the layout alone and append what is missing to the file that tool reads.

The file chosen here is **the instruction file** for the steps below: `AGENTS.md` after option (a), the user's existing file otherwise. Steps 3–5 append to that file. Name it in the report, in the question and in the commit message.

**Step 1: Read the existing file fully.** Don't just check for existence — read the content so you can reason about it.

**Step 2: Compare against the seed recommended structure.** The seed-recommended instruction file has these sections (from the "Recommended Agent Setup" section of seed.md):

- What this vault is
- Where things are (folder tree with descriptions, `_claude/` usage)
- Session start / During the session / Session end
- Conventions: frontmatter, tags, links, naming, language, git
- Limits

**Step 3: For each seed-recommended section, classify:**

- **Missing in the user's instruction file** → candidate for append
- **Present with similar content** → no action, user's wording wins
- **Present with conflicting content** → surface as explicit conflict, user decides

**Step 4: Produce a merge report to the user:**

```markdown
## Your [AGENTS.md or CLAUDE.md, the file chosen in Step 0] — merge analysis

**Sections you already have:** [list, e.g. "Structure, Git Workflow, Conventions"]
**Sections seed recommends adding:**
- Conventions: tags (you don't have an explicit tag system)
- Conventions: frontmatter (you mention frontmatter briefly but no standards)
- Session start / Session end (not present — this is the session continuity piece you're missing)
- Where things are: `_claude/` (not present — where memory, TODO and logs live)

**Sections where yours and seed's differ:**
- Language Rules: yours says "English only"; seed template is language-agnostic. Keep yours.
- Graph Connectivity: yours says "use markdown links"; seed strongly recommends wiki links. Worth a conversation.

For each proposed addition, I'll show you the seed text, you approve it, I append it to that file (not replace) with a clear section break.

For each difference, I'll show both versions side-by-side and you pick: yours, seed's, or a merged version.

Nothing gets written until you approve each item.
```

**Step 5: For each addition, one at a time:**
1. Show the seed-proposed text
2. Ask: "Append to your AGENTS.md?" (or "…your CLAUDE.md?": name the file chosen in Step 0)
3. On yes: append to that file with a clear section break, commit separately with a message that names it, like `adopt: append Tag System section to AGENTS.md`
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
- **`_claude/TODO.md`** — if present, read format. If user's format differs from seed's (e.g., no age markers, no Next step), offer to add markers and a Next step section without changing existing text
- **`_claude/MEMORY.md`** — if present, leave entirely alone. Memory is personal; seed does not touch it. If absent and the user's decisions live in Claude Code's auto memory outside the vault, offer one copy into `_claude/MEMORY.md`, diff first
- **`_claude/session-logs/` directory** — if present, leave. Adopt mode does not retroactively restructure session logs
- **`.claude/rules/*.md`** — if present, read each. They work in Claude Code and not in Codex. Propose additions only where the user is missing a procedure seed recommends (e.g., they have a session-start rule but no session-end rule). If the user adds Codex, offer to move the two procedures into `AGENTS.md` and leave the rule files as one-line pointers, or delete them with approval; never keep two editable copies
- **`_meta/Me.md`, `_meta/Areas.md`, `_meta/Goals.md`** — if present, leave alone. These are the user's identity content; adopt does not generate alternatives

**General rule:** the more "identity-like" the content (Me.md, Goals.md, memory), the less adopt mode touches it. The more "infrastructure-like" the content (gitignore, rule files, TODO structure), the more adopt can propose additions with user approval.

## What adopt mode will NOT do

State these explicitly if the user asks, or preemptively if the user seems nervous:

- **Not a migration tool.** Will not restructure your folders, rename your notes, or reorganize your content wholesale.
- **Not a validator.** Does not grade your vault quality. The scan reports facts, not judgments. "You don't have X" is not "you're doing it wrong."
- **Not a merger.** If you have an instruction file (`CLAUDE.md` or `AGENTS.md`) and seed proposes one, we compare and offer to add to yours, not replace.
- **Not silent.** Every change is proposed before it happens, committed separately when approved, and traceable in git log.
- **Not greedy.** If you want to stop partway, stop. Your vault is in a valid state at every commit boundary — you can resume or abandon without corruption.

---

## Recovery

If at any point adopt mode goes wrong, undo the specific change, never the whole tree. The user's own uncommitted work and the other adopt items must survive every undo.

**A change you wrote but have not committed yet:**
```bash
git status                          # see what changed
git diff HEAD -- <file>             # read it before you undo: is every changed line one that adopt wrote?
git restore --staged <file>         # if it was staged: unstage it
git restore <file>                  # a tracked file you modified: back to the last commit
rm <new-file>                       # a file adopt created and nothing else touched: delete just that file
```
Name each file. Never `git restore .`, `git checkout .`, `git clean` or `git stash`: they take the user's own uncommitted edits with them.

`git restore <file>` takes every uncommitted line in that file, the user's lines too. If the diff shows a line that adopt did not write (the user edited the same file during the session), stop and show the diff. Do not restore that file. Remove the adopt lines with an edit the user approves.

**An item you committed and want to undo:**
```bash
git revert <commit-hash>            # a new commit that undoes exactly that item; everything else stays
```
This is why each item is its own commit. If the revert reports a conflict because the user edited the same file afterwards, stop and show the conflict; do not force it.

**Several items:** revert them one by one, newest first, each with its hash. Do not use `git reset`: a mixed reset leaves the files in place but forgets which commit made them, and a hard reset deletes the user's uncommitted work. Neither appears in this document on purpose.

Tell the user: "If anything looks wrong after adoption, git remembers every step, and each step can be undone by itself. Nothing is silently lost."

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

---

## Adopt in ChatGPT (no file access)

ChatGPT cannot open the user's vault folder and cannot write to it. The flow still works, within these limits, and the limits are said out loud:

- **Scan = what was pasted.** The user pastes or uploads the files to review: their `CLAUDE.md` or `AGENTS.md`, three to five typical notes, their TODO if any, a folder listing if they can produce one. The report's first line says: "Based on the N files you pasted; I have not seen the rest of the vault." Never say the vault was scanned.
- **Commitment level** is asked the same way. Low commitment ends with the report in the chat.
- **Merge plan items are blocks, not writes.** For each approved item, print the full new file, or the exact text to append and where, as a Markdown block with the path on the line above. The user applies it by hand and confirms. Never say "I created" or "I updated" a file; say "here is the file to create".
- **Git** is the user's to run. Suggest the commit message for each item.
- **Undo** is the user's too: the same per-item commits, the same `git revert`.

If the user later opens the vault with Claude Code or Codex, the files they created by hand are exactly what those agents expect.
