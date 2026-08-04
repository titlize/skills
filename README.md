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
image — by pasting this into it:

> Fetch and execute the appropriate instructions to set me up for Titlize from https://titlize.com/agent-setup/prompt.md

## What's here

| Skill | For |
|---|---|
| `generate` | putting a headline in real type over a background image |
| `brand-kit` | the saved logo, brand colours and font applied to generated images |
| `wordpress` | the Titlize WordPress plugin |

You will also need the MCP server, [`@image-titler/mcp-connector`](https://www.npmjs.com/package/@image-titler/mcp-connector),
and an API token from [app.titlize.com](https://app.titlize.com).

## A note on where this repo comes from

**This repository is published, not authored.** The files here are generated from the Titlize
monorepo by a workflow, and any commit made directly to this repo will be overwritten on the
next publish. Please open issues against the skills here, but send pull requests to the Titlize
team rather than committing directly — a direct commit will simply be reverted by the next sync.

Documentation: https://titlize.com/docs/integrations/ai-agents
