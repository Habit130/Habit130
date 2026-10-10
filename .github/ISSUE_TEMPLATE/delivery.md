---
name: Delivery contract
about: Freeze one issue-scoped delivery and its acceptance evidence
title: ""
labels: needs-triage
assignees: ""
---

Contract: AC-<issue>-v1

## Goal

<!-- Observable outcome and motivation. -->

## Scope

### Included

- <!-- Finite included work. -->

### Excluded

- <!-- Explicit non-goals. -->

## Dependencies

- <!-- Blocking dependencies or None. -->

## Independent Acceptance

- Decision: required | not required
- Rationale: <!-- Blast radius, reversibility, cross-boundary effects,
  implementation judgment, deterministic verification strength. -->

## Repository Baseline

- [ ] BASE-EVIDENCE: Execution maps every criterion to primary evidence and
  Pass/Fail. Independent Acceptance, when triggered, provides its own complete mapping.
- [ ] BASE-VERIFY: Every build, lint, test, typecheck, packaging, or focused command
  named in this issue succeeds in the required order, with identified output.
- [ ] BASE-SEVERITY: The PR introduces no independently confirmed P0/P1.
  Codex findings are confirmed or rejected with primary evidence:
  - P0: A catastrophic PR-introduced defect with system-wide or broadly
    irreversible impact, such as widespread unrecoverable data loss,
    credential exposure enabling unauthorized access, or complete loss
    of the primary product for nearly all supported use.
    It has no reasonable containment before merge.
  - P1: A concrete PR-introduced defect on a supported path breaking a core
    operation, corrupting canonical/persisted data, or violating an established
    security/privacy boundary, with substantial impact and no acceptable workaround.
  - P2/P3: Lower-severity defects, maintainability concerns, optional refactors,
    stronger tests, and out-of-contract improvements are non-blocking follow-up.
- [ ] BASE-SCOPE: Outside included scope is untouched or recorded as deferred;
  excluded scope is not implemented.
- [ ] BASE-DOCS: Behavior, interface, workflow, or constraint changes update
  authoritative documentation in the same delivery.
- [ ] BASE-PR: The PR links this issue and states Motivation, Changes, Verification.

## Ticket Criteria

- [ ] TICKET-1: <!-- Requirement. -->
  - Expected evidence: <!-- Primary artifact, command, or observable result. -->

## Verification Commands

<!-- Exact commands and required order, or N/A with reason. -->

## Contract Changes

<!-- Append version, habit decision, changed criteria, and acknowledgement.
Preserve acknowledged contract history. -->
