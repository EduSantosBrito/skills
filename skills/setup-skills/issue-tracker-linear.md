# Issue tracker: Linear

Tasks, Wayfinder maps, decision tickets, and implementation tickets for this repository live in Linear. Specifications and research use the independently selected artifact sources recorded in `.agents/artifact-sources.md`; when either source is Linear, this convention governs that artifact too. Use Linear's official remote MCP server as the primary interface and GraphQL only as a capability fallback.

Creating or changing any Linear record requires explicit user authorization immediately before the effect. Selecting Linear during setup, invoking a skill, or authorizing browser use does not imply authorization.

## Local configuration

Before using Linear, read `.agents/issue-tracker.local.md`. It contains the selected workspace, team, project, claim actor, workflow state IDs, access mode, and verified MCP capabilities. The file is intentionally gitignored because those values are repository-local metadata. If it is missing, stop with a configuration diagnostic; repository bootstrap must be completed in a separate `setup-skills` session before workflow work begins.

Keep OAuth credentials and API keys in the active client's secret store. Neither tracker file may contain credentials.

## Workflow labels

```yaml
labels:
  wayfinder-map: wayfinder:map
  wayfinder-research: wayfinder:research
  wayfinder-prototype: wayfinder:prototype
  wayfinder-grilling: wayfinder:grilling
  wayfinder-task: wayfinder:task
  spec: agent:spec
```

These names are public repository conventions. Concrete Linear label IDs are optional and belong in `.agents/issue-tracker.local.md` when the connected MCP requires them.

## Access

- **Default:** `https://mcp.linear.app/mcp`, using its interactive OAuth flow and read-write access.
- **Read-only exploration:** `https://mcp.linear.app/mcp/readonly` or a read OAuth scope. This cannot support Wayfinder, ticket publishing, triage, or review comments.
- **Fallback:** `https://api.linear.app/graphql` with a personal API key restricted to the selected team and the minimum required permissions. Keep the key in the configured secret store under `LINEAR_API_KEY`; never write it to this file, a committed `.env`, a ticket, a comment, or the temporary wizard.

Discover the tools exposed by the connected MCP client rather than hardcoding tool names. Use GraphQL only for a required operation the active MCP toolset does not expose, commonly relationship or hierarchy mutations. Re-check MCP capabilities when Linear adds support.

The Linear Agent APIs are not required for this tracker integration. They are a separate developer-preview path for deploying an app user that receives mentions or delegated issues; adopt them only when native agent identity is itself a product requirement.

## Setup wizard

When Linear is selected during repository bootstrap, `setup-skills` ends its current phase with a self-contained handoff to a fresh `wizard` session. The wizard may generate an ephemeral bash wizard under the operating system's temp directory. It must:

1. detect the current agent client and existing MCP configuration;
2. open Linear's official MCP setup instructions for the human and configure `https://mcp.linear.app/mcp`;
3. guide the human through OAuth without capturing or printing the OAuth token;
4. discover the workspace, team, team key, team ID, workflow states, the team's active projects, and available MCP operations;
5. derive a proposed project name from the repository, then offer: create that project, use one of the team's active existing projects, or use no project; lead with the best fit and allow the proposed name to be edited;
6. ask before creating a project, creating or changing labels, changing workflow configuration, or creating verification issues; never treat trashed or archived projects as active choices;
7. when approved, verify create, read, update, comment, parent/sub-issue, and blocking-relation operations with temporary issues, then remove or archive those issues; when the current MCP exposes neither operation, cancel the clearly marked verification issues so no open work remains;
8. leave either a durable, non-secret result or an inline self-contained result brief; repository configuration remains owned by `setup-skills`;
9. delete its ephemeral script after successful verification;
10. hand off to a fresh `setup-skills` session in resume mode with the result pointer or inline brief.

No transient repository file may carry the handoff. The wizard may open official URLs for the human running it; it is not authorization for agent-driven browser automation. Creating or changing any Linear record requires explicit authorization immediately before that effect.

## Conventions

- Issues always belong to the configured Linear team. Use the configured project only when one is recorded above.
- Use the human-readable identifier such as `ENG-123` or the canonical URL in conversation. Retain Linear's opaque ID in API operations when required.
- Read the issue description, labels, state, assignee or delegate, relations, parent, children, and comments before acting.
- Use Linear comments for discussion and durable resolution notes.
- Use workspace labels for workflow-wide labels and team labels only for genuinely team-specific vocabulary.
- Use native parent/sub-issue hierarchy and native `blocking` / `blocked` relations. Do not reproduce these relationships only in prose when the API capability is available.
- Re-read an issue after claiming or mutating it when concurrent agents may be working the same frontier.

## When a skill says "publish to the issue tracker"

After obtaining explicit authorization at the effect boundary, follow `.agents/artifact-sources.md`. Linear specifications are issues labelled `agent:spec`; Linear research uses `wayfinder:research`. Implementation tickets link to the authoritative specification.

## When a skill says "fetch the relevant ticket"

Fetch the issue by identifier, URL, or opaque ID with its description, comments, labels, state, hierarchy, and relations. Follow referenced Wayfinder decisions when the source is a map or spec.

## Triage

Use `.agents/triage-labels.md` for canonical role mappings. Prefer existing workspace labels. When creating the canonical state roles, place them in a Linear label group so exactly one state-role label can apply at a time; keep category roles in a separate group or map them to existing labels.

Do not replace the team's normal Linear workflow states with the triage role vocabulary. Labels express agent readiness; workflow states continue to express the team's operational process.

## Wayfinding operations

Used by `wayfinder`. The **map** is one parent issue and its decision tickets are native sub-issues.

- **Map:** create an issue labelled `wayfinder:map`. Its description holds Destination, Language and locale, Notes, Decisions so far, Not yet specified, Deferred downstream, Out of scope, and Status.
- **Decision ticket:** create a sub-issue under the map with exactly one `wayfinder:<type>` label: `research`, `prototype`, `grilling`, or `task`.
- **Blocking:** create a native blocking relation from the blocker to the blocked decision. The fallback GraphQL integration must preserve the same native relation.
- **Frontier:** list the map's open sub-issues; exclude completed or canceled issues, issues with incomplete blockers, and issues already claimed under the configured claim convention.
- **Claim:** before doing work, move the issue to the configured started state and assign or delegate it to the configured claim actor. Re-read it immediately; if another actor claimed it, release it and choose another frontier issue.
- **Resolve:** post the resolution as a comment, move the decision to the configured completed state, and append one linked gist to the map's Decisions so far.
- **Definition ready:** after explicit authorization for the Linear mutation, update the map status in its description, then route to `to-spec` with the map URL. Technical decisions remain under Deferred downstream rather than open Wayfinder tickets.

## Ticketing operations

Used by `to-tickets` and `implement`.

- If the authoritative specification is a Linear issue, create tracer-bullet tickets as its sub-issues; otherwise, create them under the configured parent issue and link each ticket to the authoritative specification.
- Express blocking edges with native issue relations.
- A ticket is ready when its blockers are complete and its agent-readiness label permits implementation.
- Preserve each ticket's observable outcome and acceptance criteria in the description; keep implementation discussion in comments.

## Official references

- [Linear MCP server](https://linear.app/docs/mcp)
- [Linear GraphQL API](https://linear.app/developers/graphql)
- [API keys and webhooks](https://linear.app/docs/api-and-webhooks)
- [Parent and sub-issues](https://linear.app/docs/parent-and-sub-issues)
- [Issue relations](https://linear.app/docs/issue-relations)
- [Issue labels](https://linear.app/docs/labels)
- [Linear Agents](https://linear.app/developers/agents)
- [Agent interaction best practices](https://linear.app/developers/agent-best-practices)
