# Issue Tracker: GitHub

Issues and PRDs live in GitHub Issues for `Habit130/habit130`.
Use `gh` with explicit `--repo Habit130/habit130`.

## Operations

- Create: `gh issue create --repo Habit130/habit130 --title "..." --body-file <file>`
- Read: `gh issue view <number> --repo Habit130/habit130 --comments`
- List: `gh issue list --repo Habit130/habit130 --state open`
- Comment: `gh issue comment <number> --repo Habit130/habit130 --body-file <file>`
- Claim: `gh issue edit <number> --repo Habit130/habit130 --add-assignee @me`
- Labels: `gh issue edit <number> --repo Habit130/habit130 --add-label <label>`

The issue is the only acceptance-contract body.
Use the delivery issue template and protocol in `delivery.md`.
Read the issue and comments before acting; resolve dependencies before dispatch.
Where native dependencies are unavailable, record `Blocked by: #<number>`.

Execution acknowledges the contract, branch/worktree, and attempt before writing.
A complete contract is required before applying `ready-for-agent`.
Keep delivery issues open until habit merges and default-branch completion is verified.

## Pull requests as a triage surface

PRs as a request surface: no.

## Publishing and fetching

"Publish to the issue tracker" means create a GitHub issue.
"Fetch the relevant ticket" means read the issue with comments.
GitHub shares issue and PR numbering; resolve the resource type before updating it.
