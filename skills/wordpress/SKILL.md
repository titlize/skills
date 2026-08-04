---
name: titlize-wordpress
description: Install, configure and troubleshoot the Titlize WordPress plugin, which generates share images for posts automatically. Use when the user mentions WordPress, WP, a WP site, wp-admin, or a post's preview image on their WordPress blog.
---

# The Titlize WordPress plugin

Generates a share image for a WordPress post — either automatically on publish, or by hand from
the editor — and sets it as the post's preview image.

## Installing

Search for "Titlize" in **Plugins → Add New** in wp-admin, install and activate. Then open the
plugin settings and paste an API token created at `https://app.titlize.com`.

Without a token the plugin is inert: it will not generate anything and will say so. That is the
intended behaviour, not a bug.

## What it does on a post

- Uses the post's featured image as the background and the post title as the headline.
- Offers a visual editor so the author can reposition the text and preview the result before
  saving.
- Writes the generated image as the post's preview image so shared links pick it up.

## Troubleshooting, in the order worth checking

1. **No image generated.** Check the token is set in plugin settings and the post has a
   featured image. Both are required.
2. **Quota reached.** The account's monthly image quota is exhausted; the plugin reports this.
3. **The old preview is still showing.** Social platforms cache link previews aggressively.
   The image is usually correct — re-scrape the URL with the platform's own debugging tool
   before assuming generation failed.
4. **Nothing appears in the editor.** Confirm the plugin is activated for the site, and on
   multisite that it is active for that specific site.

## Working on the plugin's own code

Ask the user where their WordPress install lives. Do not guess a path, and do not edit files in
a live site without saying what you are about to change.

## What this skill does not cover

Direct API or MCP generation outside WordPress, and the saved logo, colours and fonts. Those are
separate.
