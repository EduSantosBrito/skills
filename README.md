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

## Install

Install all skills in this repository:

```bash
npx skills@latest add EduSantosBrito/skills
```

Install only `you-lost-me`:

```bash
npx skills@latest add EduSantosBrito/skills --skill you-lost-me
```

The installer asks which agent CLIs should receive the skill. It installs into the current project by default. Add `--global` to make the skill available across projects.

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

## License

[MIT](./LICENSE)
