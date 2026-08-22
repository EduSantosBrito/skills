# Maintain mode

Use this branch when Wayfinder routes a stale existing verification capability. Maintenance belongs to `create-verification-skill`; do not create or hand off to a second global maintenance skill.

## Scope and outcome

Edit only the existing project-local verification capability directory. Product code is evidence, not edit scope. End with exactly one outcome:

- **clean** — source and live coverage found no correction;
- **changed** — proven map, harness, or skill corrections remain in the working tree;
- **blocked** — coverage or safe correction could not finish, with the exact blocker.

Do not create a branch, commit, or PR unless separately requested.

## Pass

1. **Locate.** Identify the capability by its Launch/Doctor/Drive/Evidence/Cleanup contract and feature map. Several candidates require the user to select one; none returns to create mode.
2. **Index hygiene.** Compare `features/README.md` with sibling feature files; remove dead or duplicate index entries and add only evidenced omissions.
3. **Source reconcile.** For every feature, trace current public entry points, stable handles, intended outcomes, and recent relevant churn. Use read-only parallel readers only when the runtime supports owned independent work; the current owner verifies every returned citation.
4. **Live pass.** Follow the capability's own lifecycle. Doctor before the first drive, on every fresh session, and after surprising behaviour. Exercise every mapped feature through the endpoint, serializing access to shared instances. Capture evidence before cleanup and verify its survival afterward.
5. **Triage.** Apply the table below. Re-drive every harness correction and any feature whose proof contract changed.
6. **Finish.** Tear down every run-owned resource, verify retained evidence, inspect links/frontmatter/index/diff, and report coverage plus the outcome.

## Triage

| Observation | Classification | Action |
| --- | --- | --- |
| User-facing description or route no longer matches a working endpoint | Documentation drift | Correct the map and re-drive the feature |
| Endpoint works but the capability cannot drive or observe it | Harness drift | Correct the capability and prove the correction live |
| Endpoint behaviour violates the durable criterion | Product defect | Report the defect; keep the truthful criterion and do not edit product code |
| A prerequisite is unavailable or unauthorized | Unreachable/blocked | Record attempted route and concrete prerequisite; do not substitute a proxy |

After a failed drive, clean its residue without deleting evidence already captured. For a shared long-lived instance, clean feature residue rather than terminating work still needed by the pass. Relaunch or reset to a known state when Doctor cannot detect a wedged UI/session.

Run maintain mode because concrete drift was observed, not on an invented calendar cadence.
