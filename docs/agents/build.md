# Build and Verification

The repository currently contains Markdown governance and repository metadata.
No product build, lint, test, packaging, deployment, or CI command is configured.
Do not invent package scripts or treat unavailable checks as passed.

## Required order

1. Inspect changed files, links, paths, commands, and contract scope.
2. Run whitespace and governance structure checks.
3. Verify ignore behavior.
4. Inspect the final diff and live GitHub settings.
5. After commit and push, verify the exact PR head and delivery evidence.

## Commands

| Task | Command | Evidence / notes |
| --- | --- | --- |
| Worktree status | `git status --short --branch` | Branch and existing changes |
| Whitespace | `git diff --check` | Before staging |
| Staged whitespace | `git diff --cached --check` | Before commit |
| Root instruction budget | `wc -l -c AGENTS.md` | Near 100 lines; below 12 KiB |
| Main sections | `grep -n '^## ' AGENTS.md` | Exactly six required sections |
| Ignore rules | `git check-ignore .local/agent-context.md docs/orchestration/handoffs/AC-0-v1-a1-execution.md` | Both ignored |
| Tracked README exceptions | `git check-ignore .local/README.md docs/orchestration/handoffs/README.md` | No output; exit 1 is expected |
| Final staged scope | `git diff --cached --stat` | Only confirmed artifacts |
| Final delivery diff | `git diff origin/main...HEAD` | Inspect after commit |

## Operational constraints

No dependency installation, network-link crawler, product build, or deployment
is required for the current baseline. Markdown local links are inspected
against repository paths; external links are not treated as guaranteed availability.

There are no configured machine-level shared resources.
Parse changed JSON and run `opencode debug config` only if a future delivery
changes runtime configuration. Update this guide when real executable paths appear.
