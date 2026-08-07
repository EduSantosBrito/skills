# Agent Skills

[![skills.sh](https://skills.sh/b/EduSantosBrito/skills)](https://skills.sh/EduSantosBrito/skills)

> Heavily opinionated, intentionally small skills for coding agents.

This repository contains portable [Agent Skills](https://agentskills.io/) that solve specific communication and engineering problems. Install them with [skills.sh](https://skills.sh/) in any supported agent CLI.

## Available skills

### [`you-lost-me`](./skills/you-lost-me/SKILL.md)

Use this skill when an agent's explanation is difficult to follow. It asks the agent to explain the same idea again with the context you are missing.

Before replying, the agent:

1. identifies your language and locale from the conversation;
2. checks official standards bodies for the latest local adoption of ISO 24495-1;
3. uses that verified adoption, or the latest international edition when no local adoption is available;
4. re-explains the idea in your language and uses the shared vocabulary from `CONTEXT.md` when available.

The skill runs only when you invoke it. Your agent will not select it automatically.

### [`explore`](./skills/explore/SKILL.md)

Use this skill to understand a software vertical or module end to end before changing it. The agent traces one concrete scenario through entry points, domain rules, data, persistence, integrations, and observable outcomes.

The explanation uses the applicable adoption of ISO 24495-1, visual maps, source citations, explicit uncertainty, and a minimal reading path. Exploration is read-only and runs only when you invoke it.

### [`wayfinder`](./skills/wayfinder/SKILL.md)

Use this skill as the entry point for work of any size. It classifies the actual work state and routes a small, clear task directly to the fitting workflow; when definition decisions remain, it opens a scoped Wayfinding map with shared domain language, grilling, automatic research, and a localized next-session handoff.

User-facing communication follows the applicable local adoption of ISO 24495-1, falling back to the latest international edition. The skill keeps definition, specification, ticketing, and implementation at their own depths. It runs only when you invoke it.

### [`product-design`](./skills/product-design/SKILL.md)

Use this specialist lens when work defines, prototypes, implements, or reviews a user-facing interface or growth journey. It contributes stage-appropriate product-design decisions without replacing Wayfinder, specification, ticketing, implementation, or Hunk review ownership. Direct product-design audits remain read-only.

The skill consolidates Emil Kowalski's design-engineering material, Revenue-Centric Design, and selected contextual heuristics from Taste Skill. Its structure follows `writing-for-agents`: a short stage-aware contract routes to progressively disclosed foundations, motion, redesign, visual-direction, growth, and measurement references.

### [`setup-skills`](./skills/setup-skills/SKILL.md)

Use this skill once per repository to configure the Wayfinder-led workflow: GitHub, GitLab, Linear, or local issue tracking; triage vocabulary; domain documentation; stage ownership; localized handoffs; automatic research; custom-skill priority; and Hunk review integration. Linear setup uses a temporary `wizard`, official MCP OAuth, and a scoped GraphQL fallback when required.

### [`code-review`](./skills/code-review/SKILL.md)

Use this skill to review a branch or diff through Hunk along independent Standards and Spec axes. It loads the installed Hunk skill dynamically, runs both reviews in isolated subagents, and writes actionable findings back as Hunk comments.

## Way of working

Run `setup-skills` once in each repository, then start every piece of work with `wayfinder`. It classifies the current work state before choosing the minimum sufficient route: clear work goes directly to the fitting workflow, while definition fog opens scoped domain modeling, grilling, automatic research, and a durable decision map.

The main build flow remains:

```text
wayfinder → to-spec → to-tickets → implement → code-review
```

Bugs, incidents, reviews, research questions, prototypes, and already-specified work can enter at their fitting stage instead. Each handoff tells the user—in their language and locale—which command to run in a fresh session. Use `explore` as a read-only on-ramp when the code path or data model must be understood before deciding or changing anything.

`product-design` is a specialist lens, not a mandatory stage. Wayfinder routes visual or interaction uncertainty to `prototype`, defined interface work to `to-spec` or `implement`, and a requested read-only experience audit to `product-design review`. The owning workflow keeps its normal artifact and handoff while the model loads the relevant product-design references. Reviews of implemented diffs still run through Hunk: start a live Hunk session, then invoke `code-review`.

## Install

Install all skills in this repository:

```bash
npx skills@latest add EduSantosBrito/skills
```

Install only one skill:

```bash
npx skills@latest add EduSantosBrito/skills --skill you-lost-me
npx skills@latest add EduSantosBrito/skills --skill explore
npx skills@latest add EduSantosBrito/skills --skill wayfinder
npx skills@latest add EduSantosBrito/skills --skill product-design
npx skills@latest add EduSantosBrito/skills --skill setup-skills
npx skills@latest add EduSantosBrito/skills --skill code-review
```

The installer asks which agent CLIs should receive the skill. It installs into the current project by default. Add `--global` to make the skill available across projects. Restart or reload the agent after installation. In Prime Agent, invoke a loaded skill as `/skill:<name>`—for example, `/skill:wayfinder` or `/skill:setup-skills`; other clients may expose `/wayfinder`-style aliases.

## Repository structure

Each skill is a self-contained directory:

```text
skills/
  <skill-name>/
    SKILL.md
    agents/          # Optional agent-specific metadata
    references/      # Optional supporting documentation
    scripts/         # Optional helper scripts
    assets/          # Optional templates and data
```

Only `SKILL.md` is required.

## Credits

`you-lost-me` is adapted from Matt Pocock's [`wait-what`](https://github.com/mattpocock/skills/tree/main/skills/productivity/wait-what) skill. It keeps the same corrective idea with a name that I like more.

`explore` follows Matt Pocock's [`writing-for-agents`](https://github.com/mattpocock/skills/tree/main/skills/productivity/writing-for-agents) guidance. Its visual and explanatory approach is informed by ISO 24495-1, the [C4 model](https://c4model.com/), [arc42](https://arc42.org/), and [Diátaxis](https://diataxis.fr/).

`wayfinder` adapts Matt Pocock's [`wayfinder`](https://github.com/mattpocock/skills/tree/main/skills/engineering/wayfinder) and [`ask-matt`](https://github.com/mattpocock/skills/tree/main/skills/engineering/ask-matt) skills. Its structure follows [`writing-for-agents`](https://github.com/mattpocock/skills/tree/main/skills/productivity/writing-for-agents).

`product-design` consolidates MIT-licensed material from [Emil Kowalski's skills](https://github.com/emilkowalski/skills), custom-licensed [Revenue-Centric Design](https://github.com/heliocosta-dev/revenue-centric-design), and selected MIT-licensed ideas from [Taste Skill](https://github.com/Leonxlnx/taste-skill). [Agents with Taste](https://emilkowal.ski/ui/agents-with-taste) and [`writing-for-agents`](https://github.com/mattpocock/skills/tree/main/skills/productivity/writing-for-agents) informed its editorial structure. See its bundled `SOURCES.md` and license files.

`setup-skills` and `code-review` adapt Matt Pocock's corresponding engineering workflows. The review integration uses the locally installed [Hunk](https://www.npmjs.com/package/hunkdiff) skill.

## License

The repository's original material is [MIT](./LICENSE). `product-design` also contains adapted material under separate terms; its [`SOURCES.md`](./skills/product-design/SOURCES.md) and bundled license files govern those portions. Do not represent the complete `product-design` directory as MIT-only.
