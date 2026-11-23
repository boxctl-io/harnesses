# boxctl harnesses

Rules for Claude Code running on a [boxctl](https://github.com/boxctl-io/boxctl-cli)
box, kept out of your own `~/.claude`. Each top-level directory is one
harness, named by the directory:

    boxctl claude --harness <name>          # this repository's main branch
    boxctl claude --harness <name>@<ref>    # a branch, tag or commit

A harness directory holds any of:

| File                    | Goes to on the box                                     |
|-------------------------|--------------------------------------------------------|
| `CLAUDE.md`             | `/etc/claude-code/CLAUDE.md` (managed memory)          |
| `managed-settings.json` | `/etc/claude-code/managed-settings.json`               |
| `agents/ skills/ commands/` | `~/.claude`, on top of your own configuration      |
| `model.json`            | read by boxctl: `{"model": "...", "effort": "..."}`    |

`README.md` is ignored. boxctl downloads a harness once per commit and keeps
it under `~/.boxctl/harness-cache`. A directory of the same name under
`~/.boxctl/harness` wins over this repository's.

## Harnesses

- [`pr-only`](pr-only/) -- pull request, never merge. The default for
  unattended runs (`--goal`, `--issue`, the backlog).
