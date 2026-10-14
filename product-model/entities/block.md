---
relations:
- entity: poll-vote
  verb: collects
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: components/Blocks/BlockCommands.tsx
- kind: code
  role: implementation
  target: src/replicache/mutations.ts
- kind: code
  role: implementation
  target: src/replicache/attributes.ts
---

# Block

One piece of a page: text, a heading, a list item or quote, an image or gallery, a link, embedded website or HTML, a button, a divider, a poll, math, code, a date and time, a page link or drawing, a Bluesky post, or a publication block such as a post list, subscribe form or recommended publications.

## Information kept

- **Type** — what kind of block it is
- **Content** — its text with formatting, links, mentions and footnotes, or its media, link, code or settings
- **Position** — where it sits on its page
- **Poll options** — a poll's options, which writers add and remove
