---
name: titlize-brand-kit
description: Configure the saved Titlize brand assets — logo, brand colours and font — that get applied to generated images. Use when the user asks about their logo, brand colours, fonts, or making generated images match their visual identity.
---

# Titlize brand assets

A Titlize account carries one saved set of brand assets. Once saved, they apply to images the
account generates, so the user does not restate them every time.

## What can be saved

- **A logo.** Overlaid on generated images. The corner is configurable, and so is its opacity —
  a logo at full strength over a busy photo usually looks worse than one at 60–80%.
- **Brand colours.** Used for the text and the gradient behind it.
- **A font.** Chosen from the bundled typefaces.

## Reading and changing them

The saved assets live on the user's account and are edited in the dashboard at
`https://app.titlize.com` under the brand section. Send the user there for changes — do not try
to reconstruct their identity from guesses.

When generating, per-image overrides beat the saved values. Prefer the saved ones unless the
user explicitly asks for something different for one image.

## Judgement worth applying

- Ask before changing anything saved. These settings affect every future image, not just the
  one in front of you.
- A logo needs contrast against the corner it sits in. If the background is busy there, suggest
  a different corner rather than a bigger logo.
- If the user has no saved assets, that is fine — generation works without them. Do not treat
  it as an error to fix.

## What this skill does not cover

Actually rendering an image, and the WordPress plugin. Those are separate.
