# AGENTS.md

Local OpenCode sessions inherit `~/.config/opencode/AGENTS.md`.
This file contains habit130-specific boundaries, workflow rules,
review invariants, and context routing. Repository governance is
self-contained; installed initialization skills are not runtime dependencies.

## Repository boundary

- This Git repository owns habit130's GitHub Profile README and related
  static assets. It is independent of the parent Projects repository.
- Product responsibility, non-goals, and domain terms live in `CONTEXT.md`.
- No independent website, deployment, or dynamic generation is configured.
- Public profile content uses only personal information confirmed by habit
  for publication. Preserve applicable licenses and attribution for reused assets.
- Governance lives in AGENTS, CONTEXT, docs, and GitHub templates.
  Do not put delivery protocols or internal handoffs in the profile README.
- Credentials never enter repository files, issues, or handoffs.

## Session roles

- Every writing session declares one role in its initiating prompt:
  **Orchestration**, **Execution**, or **Acceptance**.
- **Orchestration** owns issue scope, governance artifacts, and frozen
  contracts/handoffs; it does not implement or repair product content.
- **Execution** owns one issue, branch/worktree, delivery surface, and active
  writer; it implements, verifies, and repairs within the frozen contract.
- **Acceptance**, when required, independently checks that contract and writes
  tracker acceptance records only; it never edits or repairs the delivery.
- habit starts Execution and Acceptance and is the sole squash-merge authority.
  See `docs/agents/delivery.md` for the complete protocol.

## Git remotes and workflow

- `origin` = `https://github.com/Habit130/habit130.git`,
  the write remote and PR target; default branch is `main`.
- Local `main` tracks `origin/main`.
- Start independent deliveries from the latest `origin/main` using
  `<type>/<kebab-slug>`; do not use stacked PRs.
- Every post-bootstrap delivery has one frozen issue contract, branch, and PR.
- Use English Conventional Commits and English PR text.
  PRs contain Motivation, Changes, Verification, and `Closes #<issue>`.
- Agents may branch, commit, push, and create/update PRs.
  No agent merge, auto-merge, force-push, or remote history rewriting.
- habit squash-merges. Orchestration records completion only after verifying
  the delivery on `origin/main`, then cleans its local worktree/branch.
- GitHub settings enforce PR-only main, squash-only merging, no force-push
  or deletion of main, and automatic deletion of merged feature branches.
  Unsupported or failed enforcement must be reported, not assumed.

## Code Review Rules

- Report a finding only when the delivery introduces a concrete P0/P1 in a
  supported path. State trigger, impact, primary evidence, and safe path or
  exception. Style, optional refactors, and stronger-than-contract tests are
  non-blocking follow-up; severity definitions live in the issue and delivery guide.
- Flag publication of unconfirmed private personal information when it violates
  the established privacy boundary. Safe path: publish only habit-confirmed
  public information or omit the information.
- Flag reuse that violates established license or attribution requirements
  when it meets the P0/P1 threshold. Safe path: satisfy applicable terms,
  obtain permission, or use original/appropriately licensed material.

## Agent skills

Load only the guidance triggered by the current task.

| Task | Required context |
| --- | --- |
| Issue tracker operations | `docs/agents/issue-tracker.md` |
| Triage or tracker labels | `docs/agents/triage-labels.md` |
| Planning, dispatch, handback, Acceptance, repair, or parallel delivery | `docs/agents/delivery.md` |
| Build, lint, test, packaging, or CI | `docs/agents/build.md` |
| Domain terms, boundaries, or architectural decisions | `docs/agents/domain.md`, then relevant `CONTEXT.md` and `docs/adr/` entries |

## Shared-state gate

Parallel Execution uses a separate worktree per issue.
Before dispatch, Orchestration allocates exclusive ownership of every applicable
machine-level shared resource. None is currently configured.
New generators, caches, ports, or output directories require an explicit
allocation before parallel use. Machine-specific instances belong only in
gitignored `.local/agent-context.md`.
