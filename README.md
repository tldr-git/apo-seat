# APO Seat Kit — 10-minute setup

*From Tim Reilly, CloneTech Inc. The APO ("Agentic Product/Program
Officer") is the Claude Code role that plans your work, spins up and
coordinates builder agents, quality-gates everything, and hands you
one board with exactly what needs your eyes — so you review finished
work instead of supervising work-in-progress.*

## Prerequisite

Set up "legible commits" first — it is included here as
LEGIBLE-COMMITS.md (5 minutes, one CLAUDE.md paste) and also lives in
its own repo, https://github.com/tldr-git/legible-commits, if you want
to pull its updates separately. The APO assumes commits explain WHY
and serve as institutional memory.

**How an agent knows whether it's already installed:** the paste
leaves a heading in the repo's `CLAUDE.md`, exactly
`## Commits & comments are institutional memory`. If that heading is
present, skip this step; if absent, paste LEGIBLE-COMMITS.md's block
into `CLAUDE.md` first. No guessing from git history.

## Setup (once per project)

0. **Clone the kit** (keep the clone; your APO uses it to self-update):
   ```
   git clone https://github.com/tldr-git/apo-seat.git ~/apo-seat
   ```
   Updates later are just `git -C ~/apo-seat pull` — and your APO checks
   for them itself on boot (see APO.md §6).

0b. **A private GitHub remote, from day one.** The decision log is only
   useful if it outlives the laptop and other people's agents can read
   it. In the repo: `gh repo create <name> --private --source . --push`
   (Private is the standard; public only if you mean to publish). From
   here on, committed means pushed; see LEGIBLE-COMMITS.md.

1. **Copy the seat into your repo:**
   ```
   your-repo/
     apo/
       APO.md           ← from this kit
       apo-memory.md    ← create empty, one line: "# APO seat memory"
   ```

2. **Paste this block into your project's `CLAUDE.md`** (create the
   file at the repo root if you don't have one):

   ```markdown
   ## The APO seat
   When addressed as "APO" (or when coordinating multi-agent work),
   load `apo/APO.md` and `apo/apo-memory.md` FIRST — they are the
   seat's identity and memory and override default behavior. The APO
   maintains its own memory file across chats; other agents in this
   repo treat the session named "APO" as their coordinator.
   ```

3. **First run.** Open a terminal in the repo, run `claude`, paste:

   > Name it exactly "APO" — set that as this session's title yourself
   > with the session-title tool. You are the APO. Read apo/APO.md and
   > apo/apo-memory.md, then initialize the seat: record your own
   > stable session id in apo/agents.md, scan this repo for what's in
   > flight, ask me what you need to know to seed the Today's Builds
   > board, then publish it, tell me what I now have and how you'll work with me,
   > and name the model you are running.

   The APO scans the repo, asks you three questions (what you want to
   exist, what's already underway, what you'll review first), publishes
   the board seeded from your answers, and starts its memory file. On
   day one the review rail is empty and says so; it fills as builders
   report and you give the APO work. Done.
   Before the first commit the APO establishes who you are for the
   `Collaborators:` line (git config, the GitHub remote, or `gh`; if none
   answers, it asks you once and records your handle in apo-memory.md).
   (Add one line to apo/apo-memory.md so self-update works, filling in
   the newest tag of the clone, which `git -C ~/apo-seat describe --tags`
   prints: `kit source: https://github.com/tldr-git/apo-seat.git ·
   installed: <that tag>`)

## Which model runs which seat (this is where the efficiency comes from)

Set the model BEFORE you paste a kickoff (the model picker in the app,
or `/model` in a terminal session). Recommended:

- **APO: the newest, strongest model, at high effort** (as of this
  writing, Claude Fable 5.1, high).
- **Builders: a solid, fast model, at high effort** (as of this
  writing, Claude Opus 4.8, high).

Why the split, since it is the whole point of the setup:

- The APO is the judgment seat. It reads everything once, decides
  what is worth your attention, verifies builders' claims against
  the actual artifact, and harvests your feedback into rules. Every
  mistake there costs YOUR time, the scarcest input in the system.
  There is exactly one of it, so its per-token cost barely matters
  and its quality matters completely.
- Builders do bounded, well-specified work at volume: the APO has
  already turned the ambiguity into a charter, so they need
  reliability and speed on a clear task, not the best judgment
  available. There are many of them and they run for hours. Their
  per-token cost is where the money goes, and a solid model at high
  effort is very good at a well-specified task.
- Put the strongest model everywhere and you pay top rate for
  hours of routine building. Put a cheaper model on the APO and its
  misses reach you as bad review asks and unverified "done"s, which
  you then catch yourself. Strong judgment once, solid hands many
  times is the arrangement that makes one person able to run
  several builders.

Names go stale; the rule does not: the newest, strongest model on
the APO, a solid fast one on builders, both at high effort. Revisit
when a new generation ships.

## Using Codex instead of Claude Code?

Read `CODEX.md`: same seat, same files, with the plumbing swapped
(`AGENTS.md` for `CLAUDE.md`, a file mailbox for session messaging, a
local `apo/today.html` for the published board). It has its own one-paste
install.

## The one-paste install (an agent does every step above)

If you'd rather not do the setup by hand: open a terminal in your repo,
run `claude`, and paste this. The agent clones the kit, installs
legible commits only if the heading above is missing, copies the seat
in, adds the CLAUDE.md block, and does the first run.

> Name this chat exactly "APO" and set that as this session's title
> yourself with the session-title tool. Then install the APO seat from
> https://github.com/tldr-git/apo-seat.git: clone it to ~/apo-seat and
> follow its README.md setup steps in this repo, including the
> prerequisite check (install legible commits from the kit's
> LEGIBLE-COMMITS.md only if this repo's CLAUDE.md lacks the heading the
> README names) and the memory line with the clone's newest tag; before
> your first commit, establish my GitHub handle for the Collaborators line
> (git config, the remote, or gh; if none answers, ask me once and record
> it in apo-memory.md); if this repo has no remote, create a PRIVATE one
> on GitHub with gh and push after every commit from now on. Then
> do the first run exactly as the README says: read apo/APO.md and
> apo/apo-memory.md, record your own stable session id in apo/agents.md,
> scan this repo for what's in flight, ask me what you need to know to
> seed the Today's Builds board, publish it, tell me what I now have and
> how you'll work with me, and name the model you are running.

## Day one — how you use it

- **Give it work, not tasks:** "here's what I want to exist" — the APO
  maps it into lanes and tells you exactly what terminals to open and
  what to paste to launch builders (it authors the kickoffs; you just
  paste).
- **Read the ▶ blocks:** every substantial reply ends with your
  actions, linked. That's the only part you must read.
- **Review on the board:** open Today's Builds, work the review rail
  top-down, highlight-and-comment to give feedback (comments reach
  the APO with context). You never have to write status queries.
- **Walk away freely:** agents finish jobs through context limits
  without you; genuinely-your-decisions come to the board or the ▶
  block. Everything else completes on its own.

## Why this isn't "a skill"

A skill loads only when invoked. A seat must be ambient (every chat
knows it) and persistent (it remembers across chats). CLAUDE.md gives
it ambience; the seat-owned memory file gives it persistence. The APO
will offer to refine its own APO.md as it learns how you work — let
it; the seat is a living document.

## One warning

The APO's power comes from being the single coordinator: builders
route questions to it, not to you. If you redirect a builder directly
mid-sprint (normal and fine), expect the builder to checkpoint the APO
about it — that's by design, so your coordinator never goes blind.
