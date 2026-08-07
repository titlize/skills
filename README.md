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

The plugin also brings the MCP server with it — you no longer need to install
[`@titlize/mcp-connector`](https://www.npmjs.com/package/@titlize/mcp-connector) separately. All
you supply is an API token from [app.titlize.com](https://app.titlize.com); `SETUP.md` walks your
agent through it after install.

## What this plugin installs and runs

Read this before installing — it is the check the plugin directory's own guidance asks you to
make, and you should be able to make it without running anything.

| What | Where it comes from | What it does |
|---|---|---|
| `generate`, `brand-kit`, `wordpress` skills | this repository | Markdown instructions. No code, nothing executed |
| `@titlize/mcp-connector`, **pinned to an exact version** | npm, published by Titlize | Runs on your machine via `npx` and calls `https://api.titlize.com` |

The connector is pinned rather than floating so that the version you install cannot change
underneath you without a new plugin release passing directory review. It is bundled, so it
resolves nothing further from the registry at launch.

**What leaves your machine.** The background image you ask Titlize to put a headline on is
uploaded to `api.titlize.com` to be composited, and the finished image is served from there. Your
API token authenticates those requests. Nothing else is sent anywhere. Privacy policy:
<https://titlize.com/privacy>.

Distributed under the MIT licence — see `LICENSE`. Use of the plugin through the Claude plugin
directory is additionally subject to the Anthropic Software Directory Terms and the Anthropic
Software Directory Policy.

## Keeping the listing honest

The directory listing for this plugin describes what it does, what it connects to, and which
environments it has actually been run in. **Those claims are re-checked whenever the listing
copy, the tools, or the set of supported environments changes** — a listing may name only
environments the plugin has genuinely been installed and used in.

## A note on where this repo comes from

**This repository is published, not authored.** The files here are generated from the Titlize
monorepo by a workflow, and any commit made directly to this repo will be overwritten on the
next publish. Please open issues against the skills here, but send pull requests to the Titlize
team rather than committing directly — a direct commit will simply be reverted by the next sync.

Documentation: https://titlize.com/docs/integrations/ai-agents
