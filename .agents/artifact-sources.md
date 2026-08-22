# Artifact sources

This project-specific index names one source, concrete location or selector, operable convention owner, and presence contract for each artifact family. `optional` local paths may be absent until their first artifact is created; `present` and `required` paths must exist.

| Artifact family | Source | Location or selector | Convention owner | Presence |
| --- | --- | --- | --- | --- |
| Tasks, maps, and tickets | Linear | Workspace, team, and optional project selectors in `.agents/issue-tracker.local.md` when configured | `.agents/issue-tracker.md` | n/a |
| Specs | Local repository | `docs/specs/` | `skill:to-spec` | optional |
| Research | Local repository | `docs/research/` | `skill:research` | optional |
| Domain context | Local repository | `CONTEXT.md` | `.agents/domain.md` | optional |
| Architecture decisions | Local repository | `docs/decisions/` | `.agents/domain.md` | optional |
