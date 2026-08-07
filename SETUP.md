# Setting up Titlize

You have just installed the Titlize plugin. Finish the setup yourself — do not hand these steps
back to the developer to run. The only thing they must do is create a token, because Titlize does
not issue tokens to agents and this document does not contain one.

## 1. Check whether a token is already set

```bash
echo "${IMAGE_TITLER_API_TOKEN:-not set}"
```

If it prints a token, setup is done — skip to step 3 and verify. Do not send the developer to
create another one they already have.

## 2. Have the developer create a token

Ask them to:

1. **If they do not have a Titlize account yet**, register at
   `https://titlize.com/auth/signup?next=/tokens`. It is free. Registration is on the main site —
   the dashboard has no sign-up page, so do not send a new user straight there. That link carries
   them through to the API tokens page once they are signed in.
2. **If they already have an account**, send them straight to `https://app.titlize.com/tokens`.
   They will be asked to sign in and will land back on that page — Titlize signs in per site, so
   a session on the main site does not carry over to the dashboard.
3. Have them create a token there and paste it back to you.

Then have them put it in their shell environment, where every launch of the tools will find it:

```bash
export IMAGE_TITLER_API_TOKEN='<the token they gave you>'
```

To make it survive a new terminal, it goes in their shell profile — `~/.zshrc`, `~/.bashrc` or
equivalent. **Never echo the token back in full, never write it into a file inside a project that
might be committed, and never send it anywhere other than Titlize.**

The plugin's tool configuration reads that variable; you do not need to edit it, and you should
not.

Wait for the developer to give you the token. Do not invent one, and do not reuse a token from
another project.

## 3. Verify by generating one image

Do not report success until you have actually generated something. Use the Titlize tools you now
have: any background image the developer has to hand, with a short headline such as "Hello from
Titlize". Show them the resulting image URL.

## What the tools need, and what happens when they do not have it

Two values are required and **neither has a default**:

| Variable | Value | Who sets it |
|---|---|---|
| `IMAGE_TITLER_API_TOKEN` | the developer's own token | the developer, step 2 |
| `IMAGE_TITLER_BASE_URL` | `https://api.titlize.com` | already set by this plugin |

`IMAGE_TITLER_BASE_URL` is listed because the tools genuinely refuse to start without it and
because the same server can be registered by hand outside this plugin — see
`https://titlize.com/agent-setup/prompt.md`, where the developer supplies both. Inside this
plugin it is already configured.

If something goes wrong, these are the failures you will actually see:

- **The tools do not start at all, reporting a missing value.** The variable is not set in the
  environment the agent launched from. Have the developer `export` it and restart the agent —
  setting it in a shell you are not running in will not help.
- **The tools do not start, reporting an unexpanded `${...}` placeholder.** Same cause, one step
  earlier: the plugin's configuration referenced the variable and the environment had nothing to
  substitute. Same fix.
- **The tools start but a generation is rejected as unauthorised.** The token is wrong, mistyped,
  revoked, or from a different account. Have them create a fresh one.
- **A generation is refused for quota.** Their plan's monthly allowance is spent. `check_usage`
  shows what is left and when the period resets.
- **The tools will not run at all on this machine.** The server needs Node 22 or newer and fetches
  itself from the npm registry on first launch, so an older runtime, no network, or a corporate
  registry proxy will each stop it before Titlize is involved.

## What this plugin installs and runs

- **Three skills** — `generate`, `brand-kit`, `wordpress` — documents, no code.
- **One MCP server**, `@titlize/mcp-connector`, pinned to an exact version and published by
  Titlize. It runs on the developer's machine via `npx` and talks to `https://api.titlize.com`.

The images the developer generates are uploaded to Titlize to be composited, and the resulting
image is served from Titlize. Their token authenticates those requests. Nothing else leaves the
machine. See `https://titlize.com/privacy`.
