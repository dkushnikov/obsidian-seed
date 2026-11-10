# Example — New Vault with ChatGPT, No Terminal

**A fictional walkthrough.** Ravi is not a real person and this is not a report from a pilot. It shows the method when the only AI is ChatGPT in a browser: the assistant writes every file as text, and the person creates the files in Obsidian by hand. The author has not run this path in the ChatGPT product; the steps follow [guides/environments.md § ChatGPT](../guides/environments.md#chatgpt), which says what is and is not verified.

---

## About Ravi

Ravi is an independent consultant. Twelve years in operations, four on his own. He has a ChatGPT Plus subscription, uses it for drafts and research, and keeps client notes in Google Docs. He does not use a terminal and does not want to.

What he wants: his own thinking about clients and his practice in one place, and an assistant that knows that context when he asks for help.

## The setup, in ChatGPT

He installs Obsidian and creates an empty vault, `Practice`. In ChatGPT he creates a Project called *Practice vault* and uploads `seed.md` (the file templates are inside it). First message:

> Follow the guide in seed.md. I have no agent with file access: I will create every file by hand. Run the questionnaire and the discovery as a conversation; when a file is ready, print it as one Markdown block with its path on the line above, and wait for me to confirm I saved it. Start with Phase 0.

### Phase 0 by hand

The assistant printed five blocks, one at a time: `AGENTS.md`, `CLAUDE.md`, `_claude/MEMORY.md`, `_claude/TODO.md`, `_claude/session-logs/2026-11-14 — Setup.md`. For each, Ravi created the file in Obsidian, pasted, and typed *"saved"*. Ten minutes. He did not understand `CLAUDE.md` (one line, `@AGENTS.md`) and asked; the answer: *"For a future agent with file access. Harmless now."*

### Discovery, as a conversation

The questions were the ones from Phase 1. His answers were about clients and about his own practice, which he had never separated. The assistant proposed `Clients/`, `Practice/`, `Patterns/` (things he notices across clients), `Learning/`, `Money/`. He kept all five.

`_meta/Me.md` came as a block; he saved it. `_meta/Areas.md` the same. After each, a line in the session log block was updated and printed again. When he said *"patterns go in Practice, not next to it"*, the assistant printed the new `_claude/MEMORY.md` with a dated line and asked him to replace the file.

### Closing

Fifty-five minutes in, he said *"wrap up"*. Three final blocks: `_claude/TODO.md` with *Next step* ("write the first client note using the profile template"), `_claude/MEMORY.md`, the finished session log. He replaced the three files in Obsidian.

Then one more step the terminal users do not have: in the Project, he deleted the old uploads of those three files and uploaded the new ones. Without that, the next chat would read yesterday's state.

## The second session

New chat in the same Project:

> Read AGENTS.md, MEMORY.md, TODO.md and the newest session log from the project files. Show the brief from the Session start section; then we continue with Next step.

The assistant's first line:

> vault context loaded (last log: 2026-11-14 — Setup.md)

Then the brief, then the client note as a block. He saved it. The session log for the day came as a block at the start and again at the end.

## What the assistant could not do, and said so

- It never changed a file in his vault. When Ravi once asked *"did you update the TODO?"*, the answer was: *"I printed the new version; you save it. I have no access to your folder."*
- It read only what was uploaded. When he mentioned a Google Doc by name, it said it could not open it and asked him to paste the relevant part.
- It kept no memory of the vault between chats beyond the Project files he re-uploaded. ChatGPT's own memory remembered that he was a consultant; it did not remember the decisions. The files did.

## Where Ravi hit friction

- **Re-uploading after every session.** The real cost of this path. He made it a habit: three files, one minute.
- **Two copies of the truth for a moment.** Between "the assistant printed the new MEMORY.md" and "I replaced the file", the chat and the vault disagreed. The rule he adopted: the file in Obsidian is the truth; a block in the chat is a proposal until saved.
- **Temptation to let ChatGPT memory carry it.** It cannot be read as a file and it is not shared with anything else. He kept the decisions in `_claude/MEMORY.md`.

## Is this example for you?

Try this path if you have no terminal and no wish for one. It is the same method with more of your own hands in it. If you later install Claude Code or Codex, the vault is ready: the same `AGENTS.md`, the same `_claude/` files, and the agent takes over the saving.
