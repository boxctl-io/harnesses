# pr-only

Claude may do anything on the box, but delivers work as a pull request and
never merges it. `boxctl claude --goal`/`--issue` and the backlog use it by
default.

    boxctl claude --harness pr-only

The deny rules in `managed-settings.json` are a guardrail (Claude is root on
the box), and they match command text, not intent: a bare `git push` from a
checkout of `main` with an upstream set isn't in the list -- `CLAUDE.md`'s
"never work on the default branch" is what covers that. So also use a
one-repo fine-grained token (`--github store`) and branch protection on
`main`.
