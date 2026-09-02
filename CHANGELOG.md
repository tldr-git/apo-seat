# Changelog

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
