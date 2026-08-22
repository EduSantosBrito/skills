# Artifact sources template

This packaged file is a rendering template, not repository configuration and not a literal projection. During bootstrap, ask for each source and location independently, replace every placeholder, and write the project-specific result to `.agents/artifact-sources.md` only after draft approval.

Local locations must be safe project-relative paths. `optional` paths may be absent until an artifact is created; `present` and `required` paths must exist. A convention owner must be either a project-relative `.agents/` file generated for the selected source or a logical skill reference (`skill:<id>`) that the active client's catalog can resolve. Selecting Linear requires projecting its convention template to `.agents/issue-tracker.md`.

| Artifact family | Source | Location or selector | Convention owner | Presence |
| --- | --- | --- | --- | --- |
| Tasks, maps, and tickets | `{{TASK_SOURCE}}` | `{{TASK_LOCATION_OR_SELECTOR}}` | `{{TASK_CONVENTION_OWNER}}` | `{{TASK_PRESENCE}}` |
| Specs | `{{SPEC_SOURCE}}` | `{{SPEC_LOCATION_OR_SELECTOR}}` | `{{SPEC_CONVENTION_OWNER}}` | `{{SPEC_PRESENCE}}` |
| Research | `{{RESEARCH_SOURCE}}` | `{{RESEARCH_LOCATION_OR_SELECTOR}}` | `{{RESEARCH_CONVENTION_OWNER}}` | `{{RESEARCH_PRESENCE}}` |
| Domain context | `{{DOMAIN_CONTEXT_SOURCE}}` | `{{DOMAIN_CONTEXT_LOCATION_OR_SELECTOR}}` | `{{DOMAIN_CONTEXT_CONVENTION_OWNER}}` | `{{DOMAIN_CONTEXT_PRESENCE}}` |
| Architecture decisions | `{{DECISION_SOURCE}}` | `{{DECISION_LOCATION_OR_SELECTOR}}` | `{{DECISION_CONVENTION_OWNER}}` | `{{DECISION_PRESENCE}}` |
