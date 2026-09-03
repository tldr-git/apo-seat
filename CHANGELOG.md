# Changelog

## v16 — a private remote from day one; committed means pushed

- LEGIBLE-COMMITS.md, README, CODEX.md, both one-paste installs: the
  standard is a PRIVATE GitHub remote created at setup (`gh repo create
  --private --source . --push`) and a push after every commit; a change
  counts as recorded only once pushed, and a "done" checkpoint on
  unpushed work is false. Public only when publishing is the intent.
- Why: Tim, 2026-09-03: "are we encouraging commits to be made to github
  via apo and legible commits, so it will be backed up and collaborative
  there?" We were not; now we are, and the reason is written down: a log
  that lives on one laptop does not survive it and no one else's agent
  can read it.

## v15 — commits are local; a remote is private unless told otherwise

- LEGIBLE-COMMITS.md: "Where the commits go." The kit never creates a
  GitHub repository or pushes; commits stay in the local .git until
  someone adds a remote. When they do, create it private unless publishing
  is the intent (`gh repo create --private`, or Private on the web form);
  an agent asked to "put this on GitHub" defaults to private and says so.
- Why: Tim, 2026-09-03: "do you know if github commits are to a private
  repo by default, when set up via our APO kit?" The honest answer was
  "the kit doesn't decide," which is a gap.

## v14 — Codex app, not only the CLI

- CODEX.md: a terminal-vs-app table. In the app a seat is a chat thread on
  the project folder, threads run in parallel, the model and reasoning
  effort are picked per thread in the composer's picker before the first
  message (profiles are CLI-only), and the board is a plain file opened
  from the path the APO gives or from Finder. First-run, builder kickoff,
  and one-paste wording cover both.
- Why: Tim, 2026-09-03: "I'm not in the terminal, I'm in the Codex app
  interface."

## v13 — the install ends with "what you now have"

- APO.md §6: the first boot ends with five plain lines on what the
  Principal just got (one place to look, how to give work, how to give
  feedback, what runs without them, what persists), then the model it is
  running, then the seeding questions. Both first-run pastes and both
  one-paste installs ask for it.
- Why: Tim, 2026-09-03, after his Codex install: "I also didn't get a
  summary of what powers I had now that the install was complete. Why did
  I install this and what does it allow me to do now?"

## v12 — the human's handle is established, never guessed

- LEGIBLE-COMMITS.md: new "Who the human is" section. The `Collaborators:`
  line needs a real handle, so the agent resolves it (git config, the
  GitHub remote, `gh api user`) and, failing all three, asks ONCE and
  records it in the seat memory. A commit with a placeholder or a guessed
  name is a broken commit. The agent identifier is the model actually
  running. The Co-Authored-By address is now vendor-neutral.
- README + CODEX.md install steps and both one-paste installs carry the
  step before the first commit.
- Why: Tim, 2026-09-03, testing on Codex: "I wasn't asked for my github
  name by codex, so wondering how it could be following legible commits
  protocol." It couldn't; the protocol assumed the handle was known.

## v11 — first live Codex run: commit the install, name the model

- CODEX.md: two gaps from the first real run (Tim, 2026-09-03, a fresh
  folder with no commits). (1) The seat installed itself but left it
  uncommitted "because the repository began with no commits": now the
  install does `git init` if needed and commits the seat files by explicit
  path as the first legible commit; an uncommitted seat is not installed.
  (2) The first reply now names the model and reasoning effort the
  terminal runs, so the Principal can see the APO/builder split is real.
  The one-paste install carries both.
- Everything else in that run was the kit behaving as designed: legible
  commits installed because AGENTS.md was absent, no lanes invented, the
  one draft found was labeled unconfirmed, the board written, the three
  seeding questions asked.

## v10 — model per seat on Codex, with the flags

- CODEX.md: each Codex terminal is its own session with its own model and
  reasoning effort (`codex --model … -c model_reasoning_effort="high"`,
  or profile files `$CODEX_HOME/apo.config.toml` / `builder.config.toml`
  with `--profile`, or `/model` mid-session), so the APO/builder model split
  works exactly as on Claude Code. First-run and kickoff pastes now name the
  profile to start with. Verified against the Codex config reference.
- Why: Tim, 2026-09-03: "do you know if these are different chats that can
  use different model strengths?"

## v9 — the seat on Codex

- New `CODEX.md`: the seat for people running OpenAI Codex instead of
  Claude Code. Same `APO.md`, same rules; a substitution table for the
  plumbing: `AGENTS.md` in place of `CLAUDE.md`; a file mailbox
  (`apo/inbox/<seat>.md`, append-only, committed by itself) in place of
  session ids and messaging; a local `apo/today.html` opened from disk
  in place of the published board, with chat quotes as the comment
  channel; no settable session titles, so names live in `apo/agents.md`.
  Its own first-run paste, builder kickoff, and one-paste install.
- README points at it.
- Why: Tim, 2026-09-02: "an APO handoff for someone who is getting
  started on their first project, but they are using Codex not Claude
  Code."

## v8 — model per seat

- README: new section "Which model runs which seat": the newest,
  strongest model at high effort on the APO (Fable 5.1 high as of
  now), a solid fast model at high effort on builders (Opus 4.8 high
  as of now), with the reasoning: one judgment seat whose misses cost
  the Principal's time, many builders doing well-specified work for
  hours where per-token cost lives.
- APO.md §3: the APO names the model to select in every launch
  instruction it hands the Principal, so the split is never left to
  the default.
- Why: Tim, 2026-09-02: "it's the whole efficiency of this set up, so
  should be recommended to the installer, along with the reasoning."

## v7 — one-paste install, detectable prerequisite

- README: the legible-commits prerequisite is now agent-detectable. Its
  paste leaves the heading `## Commits & comments are institutional
  memory` in CLAUDE.md; present = skip, absent = install from
  LEGIBLE-COMMITS.md first. No guessing from git history.
- README: the memory line no longer hard-codes a version; the agent
  fills in the clone's newest tag (`git describe --tags`), so the same
  paste works for every future version.
- README: a "one-paste install" section with the exact block a person
  pastes into `claude` in their repo; the agent does every setup step.
- Why: Tim, giving the kit to a second friend, edited the paste line to
  be universal and asked whether the agent could KNOW if legible commits
  was already set up. It can, via the heading; now the kit says so.

## v6 — day-one board seeding

- APO.md §5: on a fresh seat the board is SEEDED, not conjured. First
  version = a repo scan (git log, README, branches, TODO/spec files)
  turned into a draft map, plus three questions to the Principal asked
  once (what should exist, what's underway, what to review first). The
  review rail starts empty and says so. From then on the board has
  exactly three feeds: builder checkpoints, the Principal's asks, the
  APO's own verification of shipped work.
- README first-run paste updated to match ("scan this repo... ask me
  what you need to know to seed the board").
- Why: the v5 first-run paste said "create the Today's Builds board"
  with no rule for where day-one content comes from; a fresh APO would
  either publish an empty shell or invent lanes. (Tim's catch, 2026-09-02.)

## v5 — self-updating seat
- APO.md §6: the seat checks its source repo on boot and applies newer
  kit versions to its own files, never overwriting the Principal's
  customizations silently; proposes its own improvements upstream.
- README: clone-the-kit step; the memory line that enables self-update.
- CHANGELOG + MIT license added.

## v4 — addressing made systematic
- Two-layer inter-agent addressing: stable session ids in files,
  live peer names only as a fast path (they change on restart; UI
  titles do not propagate to them).
- Registry protocol (`apo/agents.md`); builders report their stable
  id as their first act, so every launch is a channel test.
- Kickoff wording: "Name it exactly '…' — set that as this session's
  title yourself" (auto-titling otherwise renames the chat).

## v3 — stands alone
- Removed the only external reference; the kit has no dependencies.

## v2 — first shared version
- The APO seat (delivery format, map ownership + QA gate,
  multi-builder guidance, agents finish jobs, Today's Builds board,
  seat-level memory) + LEGIBLE-COMMITS.md as the included prerequisite.
