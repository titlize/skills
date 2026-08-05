# Titlize agent skills

Skills that teach an AI coding agent to generate Open Graph and social share images with
[Titlize](https://titlize.com).

## Install

**Claude Code**

```bash
claude plugin marketplace add titlize/skills
claude plugin install titlize@titlize
```

**Everything else**

```bash
npx -y skills add titlize/skills --skill '*' --yes --global
```

Or let your agent do the whole setup — skills, MCP server, API token and a first generated
image. Tell it to fetch and follow https://titlize.com/agent-setup/prompt.md, or copy the
ready-made sentence from [the AI agents guide](https://titlize.com/docs/integrations/ai-agents).

<!--
  The onboarding sentence is deliberately NOT written out here. It is defined once, in the
  Titlize monorepo, and every surface renders it from that definition. This README is published
  into a separate repository where nothing could keep a copy in step — so a copy here would be
  the first thing to go stale. An acceptance test enforces the single definition.
-->


## What's here

| Skill | For |
|---|---|
| `generate` | putting a headline in real type over a background image |
| `brand-kit` | the saved logo, brand colours and font applied to generated images |
| `wordpress` | the Titlize WordPress plugin |

You will also need the MCP server, [`@titlize/mcp-connector`](https://www.npmjs.com/package/@titlize/mcp-connector),
and an API token from [app.titlize.com](https://app.titlize.com).

## A note on where this repo comes from

**This repository is published, not authored.** The files here are generated from the Titlize
monorepo by a workflow, and any commit made directly to this repo will be overwritten on the
next publish. Please open issues against the skills here, but send pull requests to the Titlize
team rather than committing directly — a direct commit will simply be reverted by the next sync.

Documentation: https://titlize.com/docs/integrations/ai-agents
