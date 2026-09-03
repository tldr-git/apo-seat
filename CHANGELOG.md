# Changelog

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
