# Implementation delegation

Delegate only when the work has independent slices whose coordination cost is lower than doing them serially.

## Writer isolation

Before dispatching a writer, assign one of:

- a dedicated worktree with an explicit integration owner; or
- a write-set of paths disjoint from every other writer and from mutable parent work.

If two writers need the same path, state, generated output, migration sequence, or lockfile, keep that work serial under one owner. Read-only subagents may share paths.

Each writer brief must contain the durable artifact pointer, outcome, invariants, exact write-set, prohibited paths, verification command, and return format. Children never stage, commit, amend, or push within this skill, even if the user requests it during the stage; those operations are outside the owner and require a separate workflow. Children also do not publish or create external records.

## Ownership and join

The parent owns integration, errors, cancellation, and the final result. Bound fan-out to available independent work. Wait for every child, inspect its actual diff, rerun relevant checks in the integrated workspace, and resolve contradictions against the durable artifact.

A child's self-report is not verification. Delegation is complete only when all children have a terminal result and the parent has accepted or rejected every produced change.
