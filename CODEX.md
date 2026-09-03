# The APO seat on Codex (instead of Claude Code)

*Same seat, same files, same rules. Only the plumbing changes. Read this,
then `APO.md`; where `APO.md` names a Claude Code tool, use the substitute
below.*

## What is different, in one table

| In `APO.md` (Claude Code) | On Codex, do this instead |
|---|---|
| `CLAUDE.md` at the repo root | `AGENTS.md` at the repo root (Codex reads it the same way) |
| "set the session title with the session-title tool" | Codex sessions have no settable title. The seat's NAME lives in `apo/agents.md`; each terminal announces its name in its first message and signs its file writes with it |
| stable session ids, `send_message`, `ListAgents`, `SendMessage` | there is no agent-to-agent messaging. Use the **file mailbox**: `apo/inbox/<seat-name>.md`. To message a seat, append a dated entry to its inbox file and commit; every seat reads its own inbox at the start of every turn and after every commit. The APO's inbox is `apo/inbox/APO.md` |
| the Artifact tool, "Today's Builds" as a published page | `apo/today.html` in the repo, opened in the browser from disk (`file://`). Same layout: review rail on top, lanes below. The Principal gives feedback in chat, quoting the card's title; the APO snapshots the quoted card into `apo/record.md` before editing, exactly as the seat rule says |
| comments on the published page | not available; the chat quote above is the comment channel |
| "the ▶ block at the end of every reply" | unchanged; this is text, not a tool |
| memory, `apo/apo-memory.md`, self-update from the kit repo | unchanged; `git -C ~/apo-seat pull` works the same |

Everything else in `APO.md` (planner and gate, launching builders,
checkpoint cadence, the memory ritual, model per seat) applies as written.

## Setup on Codex (once per project)

0. Clone the kit and keep it: `git clone https://github.com/tldr-git/apo-seat.git ~/apo-seat`
1. Copy `APO.md` into `your-repo/apo/APO.md`; create `apo/apo-memory.md`
   with one line `# APO seat memory` plus the kit-source line from the
   README (fill in the clone's newest tag).
2. Create the mailbox: `apo/inbox/APO.md` (empty), and `apo/agents.md`
   with one row: `APO | the coordinator | started <date>`.
3. Paste this into `AGENTS.md` at the repo root (create it if absent):

   ```markdown
   ## The APO seat
   When addressed as "APO" (or when coordinating multi-agent work), load
   `apo/APO.md`, `apo/CODEX.md`, and `apo/apo-memory.md` FIRST; they are the
   seat's identity, its plumbing on Codex, and its memory, and they override
   default behavior. Every seat in this repo reads its own inbox file under
   `apo/inbox/` at the start of each turn and treats the APO as its
   coordinator. Commit with explicit paths, never `git add -A`.
   ```

4. Copy this file too: `cp ~/apo-seat/CODEX.md your-repo/apo/CODEX.md`.
5. Legible commits: same prerequisite as the README; the heading check
   works on `AGENTS.md` instead of `CLAUDE.md`.
6. **Commit the installation.** If the folder is not a git repository yet,
   `git init` first. Then commit the seat files and `AGENTS.md` by explicit
   path, in the legible-commit format (what changed and why: "install the
   APO seat from kit <tag>"). The seat's own installation is the first
   entry in the decision log; an uncommitted seat is not installed.
7. **Say which model you are.** The first reply after setup names the
   model and reasoning effort the terminal is running (Codex shows it in
   `/model`), so the Principal can see the APO/builder split is real.

## Model per seat on Codex (yes, each terminal can run its own)

Every Codex terminal is its own session with its own model and reasoning
effort, set three ways (from the Codex config reference):

- on launch: `codex --model <model> -c model_reasoning_effort="high"`
  (`model_reasoning_effort` accepts minimal, low, medium, high, xhigh);
- as a profile: a file `$CODEX_HOME/apo.config.toml` containing
  `model = "<strongest model>"` and `model_reasoning_effort = "high"`,
  then `codex --profile apo`; a second file `builder.config.toml` with the
  solid, fast model, then `codex --profile builder`;
- mid-session: the `/model` slash command.

So the seat rule holds exactly as on Claude Code: the APO terminal on the
strongest model at high effort, every builder terminal on a solid fast
model at high effort. Make the two profile files once; every kickoff then
says which profile to start with.

## First run on Codex

Open a terminal in the repo, start `codex --profile apo` (the strongest
model at high effort; see "Model per seat on Codex" above), and paste:

> You are the APO. Read apo/APO.md, apo/CODEX.md, and apo/apo-memory.md.
> Initialize the seat: write your row in apo/agents.md, create your inbox
> at apo/inbox/APO.md, scan this repo for what's in flight, ask me what
> you need to know to seed the Today's Builds board, write it as
> apo/today.html and tell me how to open it, then tell me in a few lines
> how you'll work with me.

## Launching a builder on Codex

The APO writes the charter file and hands the Principal this kickoff to
paste into a NEW terminal running `codex --profile builder` (the solid,
fast model at high effort):

> APO: "You are BUILDER - <Name>. Read <charter path>. Your inbox is
> apo/inbox/BUILDER-<Name>.md; read it at the start of every turn. Your
> coordinator is the APO: report by appending a dated entry to
> apo/inbox/APO.md and committing. First: add your row to apo/agents.md,
> then write your first checkpoint to the APO's inbox ('booted, on <first
> task>'); that entry IS the channel test. Then start."

Since inboxes are files in one shared checkout, two rules keep them sane:
append only (never rewrite another seat's inbox), and commit the inbox
entry by itself with the path named, so it lands even while other work is
in progress.

## The one-paste install (an agent does every step above)

Open a terminal in your repo, start `codex`, and paste:

> You are setting up the APO seat on Codex. Clone
> https://github.com/tldr-git/apo-seat.git to ~/apo-seat and follow
> ~/apo-seat/CODEX.md exactly: install legible commits from the kit's
> LEGIBLE-COMMITS.md only if AGENTS.md lacks the heading "Commits &
> comments are institutional memory", copy APO.md and CODEX.md into apo/,
> create apo/apo-memory.md with the kit-source line and the clone's newest
> tag, create apo/agents.md and apo/inbox/APO.md, add the "APO seat" block
> to AGENTS.md, and commit the installation by explicit path in the
> legible-commit format (git init first if this is not a repository).
> Then do the first run as CODEX.md says: read the seat
> files, scan this repo for what's in flight, ask me what you need to
> seed the Today's Builds board, write apo/today.html and tell me how to
> open it, name the model and reasoning effort you are running, and tell
> me in a few lines how you'll work with me.
