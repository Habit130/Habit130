# Delivery Protocol

The GitHub issue is the only acceptance-contract body.

## Roles

Orchestration owns an explicit included/excluded issue scope.
An issue cannot belong to two active orchestration scopes.
It writes governance artifacts, tracker state, contracts, and handoffs;
it does not implement or repair product content.

Before dispatch, Orchestration refreshes issues, dependencies, assignees,
branches, PRs, comments, and shared state; freezes the complete contract;
records the independent Acceptance decision and rationale; allocates
branch/worktree and shared resources; publishes an immutable handoff digest.

Execution owns one issue, branch/worktree, PR, and active writer.
Before writing, it claims the issue and acknowledges contract ID,
branch/worktree, and attempt in a comment.
It autonomously implements, verifies, inspects, and repairs delivery-caused
failures within the frozen contract. Read-only helpers are allowed;
writing helpers do not share the delivery.
Missing decisions, permissions, or prerequisites pause affected work only.

Acceptance is a fresh session started by habit.
It runs checks and writes tracker acceptance records only.
It never edits or repairs the delivery.
habit starts Execution and Acceptance and is the sole squash-merge authority.

## Contract and baseline

Every post-bootstrap PR links one executable issue containing Goal,
included/excluded Scope, Dependencies, independent Acceptance decision
and rationale, six expanded BASE criteria, and finite ticket criteria
with stable IDs and expected primary evidence.

- BASE-EVIDENCE: Execution maps every criterion to primary evidence and
  Pass/Fail. Triggered independent Acceptance provides its own complete mapping.
- BASE-VERIFY: Every build, lint, test, typecheck, packaging, or focused command
  named in the issue succeeds in the required order, with identified output.
- BASE-SEVERITY: The PR introduces no independently confirmed P0/P1.
  Codex findings are confirmed or rejected with primary evidence.
- BASE-SCOPE: Outside-scope work is untouched or recorded as deferred;
  excluded scope is not implemented.
- BASE-DOCS: Behavior, interface, workflow, or constraint changes update
  authoritative documentation in the same delivery.
- BASE-PR: The PR links the issue and states Motivation, Changes, Verification.

Starting Execution from its frozen handoff acknowledges that contract version.
Material scope, criterion, evidence, or product/security-boundary changes
require a new issue contract version, recorded habit decision, new immutable
handoff, and renewed acknowledgement before dependent work resumes.
Preserve acknowledged contract history.

## Severity

- P0: A catastrophic defect introduced by the PR with system-wide or broadly
  irreversible impact: widespread unrecoverable data loss, credential exposure
  enabling unauthorized access, or complete loss of the primary product for
  nearly all supported use. No reasonable containment exists before merge.
- P1: A concrete PR-introduced defect on a supported path breaking a core
  operation, corrupting canonical/persisted data, or violating an established
  security/privacy boundary, with substantial impact and no acceptable workaround.
- P2/P3: Lower-severity defects, maintainability concerns, optional refactors,
  stronger tests, and out-of-contract improvements are non-blocking follow-up.

A Codex P0/P1 blocks only after independent Acceptance confirms trigger,
impact, primary evidence, and severity. Ordinary override comments cannot
waive confirmed P0/P1. Boundary changes require a new issue/ADR and contract.

## Codex and independent Acceptance

Use the installed Codex review mechanism when available.
For comment-triggered review, comment exactly `@codex review`.
Inspect commits, comments, reviews, checks, and status rollups;
a trigger comment is not evidence of completed review.

Record completed without P0/P1, completed with findings awaiting independent
disposition, or unavailable/incomplete.

Orchestration predeclares Acceptance using blast radius, reversibility,
cross-boundary effects, implementation judgment, and deterministic verification.
Independent Acceptance is required when predeclared, Codex reports P0/P1,
Codex is unavailable/incomplete, or there is no GitHub review path.
Every initialization delivery requires it.

When not required, complete Execution self-check plus completed Codex review
without P0/P1 supplies the technical merge recommendation.

## Handback and review boundary

Execution hands back the acknowledged contract, exact branch/PR/head,
every criterion's primary evidence and Pass/Fail, command outputs,
deferred/out-of-contract findings, and implementation decisions left open
by the contract. It leaves issue and PR open and releases write ownership.

Acceptance reads the contract, all PR commits, diff, directly affected
interaction edges, evidence matrix, verification output, and Codex review.
Execution conclusions are leads, not facts.
It produces a fresh complete matrix and finding dispositions.
It does not audit unrelated unchanged code or fail against new preferences,
stronger tests, or unlisted scenarios unless independently confirmed P0/P1.

After repair, reopen failed criteria and previously passed criteria whose
implementation, evidence, or direct interaction edge changed.
Other passes remain closed absent primary evidence of regression.

## Failure routing

- Local defect: finite correction without new design judgment;
  prefer the original Execution for one focused revision.
- Capability mismatch: fresh, genuinely stronger Execution takeover.
- Specification blocker: apply ready-for-human and await habit's decision.
- Execution-environment blocker: pause affected work without consuming an attempt.

At most three attempts: initial, one focused revision, one fresh escalated takeover.
Failure after the final available attempt moves to ready-for-human with evidence
and a recommended decision.

## Handoffs

Frozen handoffs are gitignored under `docs/orchestration/handoffs/`.
Publish repository-relative path, contract version, attempt, role, and SHA-256
on the issue. Published files are immutable.

Names:
- AC-<issue>-v<contract>-a<attempt>-execution.md
- AC-<issue>-v<contract>-a<attempt>-acceptance.md
- ORCH-<scope>-<timestamp>.md

Execution handoffs identify repository/write target, contract/scope/criteria,
branch/worktree/resources, command order/evidence, attempt, and escalation route.
Acceptance handoffs pin exact PR head, all commits/diff boundary, Execution
handoff digest, complete evidence matrix, outputs, Codex findings/status,
affected edges/settings, and record-only authority.

Replacement Orchestration handoffs carry live frontier, issues, PRs, attempts,
findings, and resource allocations; replacements refresh live state before acting.

## Completion

Acceptance Pass marks the PR ready for habit, not permission for an agent merge.
habit squash-merges. Use `Closes #<issue>`.
Orchestration records Completed only after verifying the exact delivery on
origin/main, then cleans its local worktree and feature branch.
No agent merge, auto-merge, force-push, or remote history rewriting.
