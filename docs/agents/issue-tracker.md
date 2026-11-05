# Issue tracker: GitHub

Issues, specs, and tickets for this repo live in
`galantir-spec/wingman-ai`. Use the `gh` CLI.

## Repository selection

Pass `--repo galantir-spec/wingman-ai` to issue and PR commands.
For `gh api`, use `repos/galantir-spec/wingman-ai/...` endpoints.

This clone also has an upstream remote. Keep issue operations scoped
to the configured repository.

## Issue operations

- Create: `gh issue create --repo galantir-spec/wingman-ai --title "..." --body-file <path>`
- Read: `gh issue view <number> --repo galantir-spec/wingman-ai --comments`
- List: `gh issue list --repo galantir-spec/wingman-ai --state open --json number,title,body,labels,comments`
- Comment: `gh issue comment <number> --repo galantir-spec/wingman-ai --body-file <path>`
- Apply labels: `gh issue edit <number> --repo galantir-spec/wingman-ai --add-label "..."`
- Remove labels: `gh issue edit <number> --repo galantir-spec/wingman-ai --remove-label "..."`
- Close: `gh issue close <number> --repo galantir-spec/wingman-ai`

Use a temporary UTF-8 file for multiline bodies and pass it with
`--body-file`.

When a skill says "publish to the issue tracker", create a GitHub issue.
When it says "fetch the relevant ticket", read the issue and its comments.

## Pull requests as a triage surface

**PRs as a request surface: no.**

GitHub issues and PRs share a number space. When a number is ambiguous,
resolve it with `gh pr view` and fall back to `gh issue view`, using the
configured repository.

## Wayfinding operations

- Map: one issue labelled `wayfinder:map`, holding Notes,
  Decisions-so-far, and Fog.
- Child tickets: link them as GitHub sub-issues. If unavailable, use a
  task list in the map and `Part of #<map>` in each child.
- Ticket labels: `wayfinder:research`, `wayfinder:prototype`,
  `wayfinder:grilling`, or `wayfinder:task`.
- Blocking: use native GitHub issue dependencies. Add a blocker with
  `gh api --method POST repos/galantir-spec/wingman-ai/issues/<child>/dependencies/blocked_by -F issue_id=<blocker-database-id>`.
  Obtain the database ID from the blocker's issue API response.
  If dependencies are unavailable, record `Blocked by: #<number>` in
  the child body.
- Frontier: choose the first open child in map order that has no open
  blockers and no assignee.
- Claim: assign the ticket with
  `gh issue edit <number> --repo galantir-spec/wingman-ai --add-assignee @me`.
- Resolve: comment with the answer, close the ticket, and append a
  concise decision and link to the map's Decisions-so-far.
