---
name: titlize-generate
description: Generate an Open Graph or social share image with Titlize — put a headline in real type over a background image. Use when the user asks for an og image, a link preview, a share card, a social image, or to put a title on a picture.
---

# Generate a titled image with Titlize

Titlize renders a headline over a background image and returns a hosted image URL, sized for
social link previews.

## How to call it

If the Titlize MCP server is registered, use its `generate_image` tool. Otherwise POST to the
API directly:

```bash
curl -X POST https://api.titlize.com/generate \
  -H "Authorization: Bearer $IMAGE_TITLER_API_TOKEN" \
  -F "image=@background.jpg" \
  -F "title=Your headline, set in type"
```

Note the path is `/generate` — there is no version prefix on the API.

## What to ask the user for

- **A background image.** Required. A local file, or a URL you can fetch.
- **A title.** Required. Keep it short — a headline, not a paragraph. Long titles are
  auto-sized down and get hard to read on a phone-sized card.
- **A subtitle.** Optional.

Do not invent a headline for the user unless they asked you to write one.

## Choosing a shape

| Aspect | Size | Use for |
|---|---|---|
| `og` | 1200×630 | the default — link previews on most platforms |
| `square` | 1080×1080 | feed posts |
| `portrait` | 1080×1350 | vertical feed posts |

If the user does not say, use `og`.

## Templates

`bottom-left` (default), `left`, `right`, `split`. The renderer analyses the background and
applies a gradient so the text stays readable; you do not need to pick a text colour to make
it legible.

## Quota

Every account has a monthly image quota. If a generation is rejected for quota, say so plainly
and tell the user their limit has been reached — do not retry in a loop.

## What this skill does not cover

Saved logos, colours and fonts are configured separately. The WordPress plugin is separate too.
