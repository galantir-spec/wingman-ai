# Domain docs

This repo uses a single-context domain documentation layout:

- `CONTEXT.md` at the repo root: domain glossary and context.
- `docs/adr/`: architecture decision records.

## Before exploring the codebase

Read root `CONTEXT.md` and ADRs relevant to the area being explored.

If these files or directories do not exist, proceed silently.
The `monta-domain-modeling` skill creates them when terms or decisions
are resolved.

## Use the glossary's vocabulary

Use terms defined in `CONTEXT.md` when naming domain concepts in issues,
proposals, hypotheses, and tests.

If a needed concept is missing, reconsider whether the project already
has a term for it. Record genuine gaps for `monta-domain-modeling`.

## Surface ADR conflicts

When a proposal contradicts an existing ADR, identify the ADR and explain
why the decision should be reconsidered.
