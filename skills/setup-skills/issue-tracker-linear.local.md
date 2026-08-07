# Local issue tracker configuration: Linear

This file complements `.agents/issue-tracker.md`. It contains repository-local Linear identifiers and capability results, is intentionally ignored by Git, and must never contain OAuth tokens, API keys, or other credentials.

```yaml
workspace: <name or slug>
workspace-id: <id or null when MCP does not expose it>
team: <name>
team-key: <key>
team-id: <id>
project: <name and id, or none>
access: linear-mcp
mcp-url: https://mcp.linear.app/mcp
graphql-fallback: <enabled | disabled>
graphql-key-env: LINEAR_API_KEY
claim-actor: <member, delegate, or configured convention>
states:
  triage: <name and id>
  unstarted: <name and id>
  started: <name and id>
  completed: <name and id>
  canceled: <name and id>
capabilities:
  create: <verified | unavailable | unverified>
  read: <verified | unavailable | unverified>
  update: <verified | unavailable | unverified>
  comment: <verified | unavailable | unverified>
  parent-sub-issue: <verified | unavailable | unverified>
  blocking-relation: <verified | unavailable | unverified>
  issue-delete-or-archive: <verified | unavailable | unverified>
verified-at: <YYYY-MM-DD or never>
```

Record IDs discovered from the selected team. Linear workflow states are team-specific; never infer IDs from display names. Re-run `/setup-skills` when the selected workspace, team, project, claim convention, access method, or required MCP capabilities change materially.
