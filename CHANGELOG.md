# Changelog

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
