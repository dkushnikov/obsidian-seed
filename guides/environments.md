# Environments — Claude Code, Codex, ChatGPT

The method is one: discovery, structure, conventions, foundation notes, continuity. What differs by environment is the mechanism: what the agent reads by itself, whether it can write files, and how the next chat continues. This page is that mechanism. The process itself is [seed.md](../seed.md); the existing-vault path is [ADOPT.md](../ADOPT.md).

## What every vault has, whatever the environment

| Piece | File | Why |
|---|---|---|
| Instruction file | `AGENTS.md` at the vault root, with `CLAUDE.md` holding `@AGENTS.md` | What the agent reads first: what the vault is, where things are, what to do at the start and end of a session |
| Memory | `_claude/MEMORY.md` | Decisions and preferences that must survive between sessions; the source of truth |
| Open items and next step | `_claude/TODO.md` | Items with `<!-- since: YYYY-MM-DD -->` markers; the **Next step** section is where the next session continues |
| Journal | `_claude/session-logs/YYYY-MM-DD — <topic>.md` | One file per session, created at the start, updated as the session goes |
| Foundation notes | `_meta/Me.md`, `_meta/Areas.md`, `Goals/` | Who you are, your areas, your goals |

Templates for all five are in [seed.md § Phase 0](../seed.md#phase-0-continuity-first); `seed.md` is self-contained on purpose. The state lives **in the vault**, as Markdown, so every environment sees the same files. A product's own memory (Claude Code auto memory, Codex memories, ChatGPT memory) is a supplement: when it disagrees with `_claude/MEMORY.md`, the file wins.

The `_claude/` folder name is historical, from the Claude Code-only version. It is the agent's workspace for any agent. Do not rename it in an existing vault.

Sources for the facts below, checked 2026-11-10: [Claude Code: How Claude remembers your project](https://code.claude.com/docs/en/memory), [Codex: Custom instructions with AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md), [Codex: Permissions](https://learn.chatgpt.com/docs/permission-modes), [ChatGPT: Projects](https://help.openai.com/en/articles/10169521-projects-in-chatgpt).

## Claude Code

**New vault.** Create an empty vault in Obsidian. Put `seed.md` in its root. Open a terminal in the vault folder, run `claude`, say *"Follow the guide in seed.md."* The agent reads and writes files in the folder; it asks before commands it is not allowed to run. Phase 0 of the guide creates `AGENTS.md`, `CLAUDE.md` and the `_claude/` files before discovery starts.

**What loads by itself.** `CLAUDE.md` from the vault and from every folder above it, `~/.claude/CLAUDE.md`, `.claude/rules/`, and the files they import with `@path`. Through `@AGENTS.md` the vault's instruction file loads at launch. `/context all` lists what loaded under *Memory files*. Claude Code also reads an `AGENTS.md` on its own when no `CLAUDE.md` exists in the vault or above it (v2.1.277+); a vault inside a folder that has its own `CLAUDE.md` would silently lose that, which is why the import is there.

**Continue.** Run `claude` in the vault. The instruction file's *Session start* section makes the agent read memory, TODO and the last log and show a brief. The first line of the answer should be `vault context loaded (last log: …)`.

**Memory.** Auto memory lives in `~/.claude/projects/<project>/memory/`, outside the vault, and may be off in some session types. A supplement. The vault's `_claude/MEMORY.md` is the record.

**Existing vault.** [ADOPT.md](../ADOPT.md). For a look-only pass, start with `claude --permission-mode plan` or decline every write the agent proposes; the report stays in the chat.

**Verified here.** Claude Code 2.1.319, macOS, 2026-11-10, non-interactive runs with a fictional persona: see the table at the end.

## Codex

**New vault.** Create an empty vault in Obsidian. Put `seed.md` in its root. Open a terminal in the vault folder, run `codex`, say *"Follow the guide in seed.md."* The default permission mode, *Ask for approval*, lets Codex edit files inside the folder and pauses before anything outside it or on the network. Git commits are one of those pauses: the sandbox protects `.git`, so Codex asks before each `git commit`; approve it, or run the commit yourself. The Codex app and the IDE extension open a folder the same way; pick the vault folder.

**What loads by itself.** `~/.codex/AGENTS.md` (your global file, if any), then `AGENTS.md` from the project root (the Git root, or the folder itself when there is no Git) down to the working directory, up to 32 KiB together. The vault's `AGENTS.md` therefore loads at every run. Codex does not read `CLAUDE.md` or `.claude/rules/` unless you add `project_doc_fallback_filenames = ["CLAUDE.md"]` to `~/.codex/config.toml`.

**Continue.** Run `codex` in the vault; same brief, same marker line.

**Memory.** Codex memories are local, off by default, and generated from past chats. A supplement.

**Existing vault.** [ADOPT.md](../ADOPT.md). For a look-only pass, start Codex read-only: `codex --sandbox read-only`, or `/permissions` inside the session. With that sandbox the agent cannot write, which makes "zero writes" a property of the run, not a promise.

**Skills.** Optional. Codex reads skills from `.agents/skills/` in the vault and from `~/.agents/skills/`; Claude Code reads `.claude/skills/`. The [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills) set teaches Obsidian syntax; it is a nicety, not a requirement.

**Verified here.** Codex CLI 0.166.0, macOS, 2026-11-10, non-interactive runs with a fictional persona: see the table at the end. The app and the IDE extension read the same `AGENTS.md`; they were not exercised by the author.

## ChatGPT

ChatGPT has no access to your vault folder. It reads what you paste or upload and it writes nothing to your disk. The method still works; you are the hands.

**New vault.** Create the empty vault in Obsidian yourself. Then, in ChatGPT:

1. Create a Project (recommended, so the files stay together) and upload `seed.md`, or paste it into the chat. The file templates are inside it.
2. Say: *"Follow the guide in seed.md. I have no agent with file access: I will create every file by hand. Run the questionnaire and the discovery as a conversation; when a file is ready, print it as one Markdown block with its path on the line above, and wait for me to confirm I saved it. Start with Phase 0."*
3. Create each file in Obsidian as it comes. Phase 0 gives you `AGENTS.md`, `CLAUDE.md`, `_claude/MEMORY.md`, `_claude/TODO.md` and today's session log; discovery gives `_meta/Me.md` and `_meta/Areas.md`.

**Continue.** In a new chat inside the same Project: upload the current `AGENTS.md`, `_claude/MEMORY.md`, `_claude/TODO.md` and the newest session log, or paste them. Then: *"Read the files; show the brief from the Session start section; then we continue with Next step."* Project files do not update themselves: after a session, replace the old uploads with the new versions you saved, or the next chat reads stale state. Custom instructions (Settings → Personalization) are for rules that apply to all your chats, not for vault state.

**Existing vault.** Paste the files you want reviewed (your `CLAUDE.md` or `AGENTS.md`, three to five typical notes, your TODO if you have one) and say *"Read ADOPT.md, look-only mode, based only on the files I pasted."* The report must say it covers the pasted files, not the vault. Changes come as blocks you apply by hand.

**Limits.** The assistant cannot change your vault. If a reply says a file was created or edited, it was not. ChatGPT memory may remember facts across chats; it is not a carrier for decisions, the files are.

**Verified here.** Not run by the author in the ChatGPT product on 2026-11-10. The steps above follow the Projects help page; the Markdown-bundle output was checked with a model run outside the product (see the table). A run in ChatGPT itself is the one check left for you.

## Claude Code and Codex in one vault

One `AGENTS.md` with the content, one `CLAUDE.md` with `@AGENTS.md`, one `_claude/`. Both agents read the same state and write to the same files. Never two copies of the instructions.

Product memories stay separate (Claude's in `~/.claude/projects/`, Codex's in `~/.codex/`). Neither sees the other's. That is fine as long as decisions go into `_claude/MEMORY.md`, which both read.

## Existing installs from before November 2026

Earlier versions of this guide put the session rules in `.claude/rules/session-start.md` and `session-end.md`, kept memory in Claude Code's auto memory outside the vault, and used `CLAUDE.md` as the only instruction file. Nothing is renamed or moved automatically.

- **Your `CLAUDE.md` keeps working** in Claude Code as it is.
- **Adding Codex** to such a vault: two honest options, both shown as a diff before anything changes. (a) Move the content of `CLAUDE.md` into a new `AGENTS.md`, leave `@AGENTS.md` in `CLAUDE.md`, and fold the two rule files into the *Session start* and *Session end* sections; the rule files then become one-line pointers or are deleted with your approval. (b) Keep everything and tell Codex to read `CLAUDE.md` through `project_doc_fallback_filenames = ["CLAUDE.md"]` in `~/.codex/config.toml`; the `.claude/rules/` files stay invisible to Codex, so copy their two procedures into `CLAUDE.md` once.
- **Memory.** If your decisions live only in Claude's auto memory, ask Claude once: *"Copy the decisions from your memory into `_claude/MEMORY.md`, show me the diff first."* From then on the vault file is the record.
- **Where the current decisions are**, when old and new files disagree: `_claude/MEMORY.md` in the vault. A product memory that says otherwise is stale; fix the product memory or ignore it.

## Verified runs

Runs by the author on 2026-11-10 with a fictional persona in throw-away folders, non-interactive (the persona's answers were given up front). "Verified" means the named files appeared and the named behaviour was observed in that run; it does not mean every rule is followed every time, and it is not a first-time user's experience.

| Environment | Version | What ran | Result |
|---|---|---|---|
| Claude Code | 2.1.319 | new vault from `seed.md`, first complete session; second run continues from `_claude/`; decision saved mid-session survives without wrap-up | see README § Status |
| Codex CLI | 0.166.0 | same, in a separate folder; ADOPT look-only in a read-only sandbox (zero writes), apply with per-item commits, re-run recognises the install, one item reverted | see README § Status |
| ChatGPT | — | not run in the product | steps above, unverified |
