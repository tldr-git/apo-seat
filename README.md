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
   > board, then publish it and tell me how you'll work with me.

   The APO scans the repo, asks you three questions (what you want to
   exist, what's already underway, what you'll review first), publishes
   the board seeded from your answers, and starts its memory file. On
   day one the review rail is empty and says so; it fills as builders
   report and you give the APO work. Done.
   (Add one line to apo/apo-memory.md so self-update works, filling in
   the newest tag of the clone, which `git -C ~/apo-seat describe --tags`
   prints: `kit source: https://github.com/tldr-git/apo-seat.git ·
   installed: <that tag>`)

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
> README names) and the memory line with the clone's newest tag. Then
> do the first run exactly as the README says: read apo/APO.md and
> apo/apo-memory.md, record your own stable session id in apo/agents.md,
> scan this repo for what's in flight, ask me what you need to know to
> seed the Today's Builds board, publish it, and tell me in a few lines
> how you'll work with me.

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
