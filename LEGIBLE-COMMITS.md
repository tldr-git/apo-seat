# Legible Commits — the prerequisite

*From Tim Reilly, CloneTech Inc. Set this up before the APO seat: the
whole system assumes the git history is institutional memory, because
agent context resets between sessions and the history is what
survives.*

Paste this into your project's `CLAUDE.md` (alongside the APO block):

```markdown
## Commits & comments are institutional memory

### Code comments
Explain INTENT and reasoning, never the obvious mechanics. The test:
"why would someone regret changing this?"
- Bad:  // set width to 30px
- Good: // 85% of 36px — full size competed with the letterforms;
        // this balances period-feel with brand presence
Document design tradeoffs, the user feedback that drove decisions,
and the alternatives that were rejected.

### Commit messages — a decision log, not a changelog
<what changed> — <why, in a few words>

<Body: the reasoning and context>
- options considered; what was tried and didn't work
- the feedback or insight that drove the decision
- which decisions came from the human vs the agent

Collaborators: @<human's handle> + <agent identifier>
source: session <short-id> @ <ISO-8601 timestamp>
Co-Authored-By: <agent model> <the agent vendor's noreply address>

The `source:` line is the PROVENANCE POINTER — it ties every output
back to the conversation that produced it. A confusing result months
later? Follow the pointer to the reasoning.

### Before changing anything
Read the git log first (`git log --oneline -20`, then the full bodies
of recent commits touching your files). This is how a fresh session
inherits context and avoids undoing intentional decisions.

### On shared working trees (multiple agents, one checkout)
Commit with EXPLICIT PATHSPECS in one command:
`git commit <your paths> -m "…"` — never `git add -A`, and never
split add and commit across steps. A bare commit on a shared tree
sweeps other agents' staged work under your message; naming your
paths on the commit itself bypasses the shared staging area entirely.
```

That's the whole prerequisite. The APO enforces these on every builder
it launches.

### Who the human is (establish once, never guess)

The `Collaborators:` line names a real person by handle, so the agent must
KNOW the handle before its first commit. Resolve it in this order, and
stop at the first hit: the repo's `git config user.name` / `user.email`;
the GitHub remote's owner (`git remote -v`); `gh api user --jq .login` if
the GitHub CLI is signed in. If none of those answers, ASK the human once
("what GitHub handle should commits credit you as?") and record the
answer in the seat memory file so it is never asked again. A commit that
credits `@<human's handle>` literally, or a guessed name, is a broken
commit: the whole point of the line is that a reader can find the person.
Same for the agent identifier: name the model actually running (Codex
sessions show it under `/model`; Claude Code under `/status`).

