---
relations:
- entity: recommendation
  verb: receives
  cardinality: one-to-many
- entity: post-comment
  verb: receives
  cardinality: one-to-many
- entity: poll-vote
  verb: collects
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/utils/publishLeaflet.ts
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/page.tsx
---

# Post

A published Leaflet: a record in its author's Bluesky account (a publication's posts live in the owner's account), read at its own address. A post of a publication appears in it; a standalone post is a Looseleaf on its author's profile.

## Information kept

- **Title** — the post's title
- **Description** — its description
- **Tags** — the tags it is filed under
- **Cover image** — the image shown when it is shared
- **Published at** — its publish date, which may be backdated
- **Content** — its pages and blocks as published
- **Address** — where it is read: under its publication's address, or on leaflet.pub for a Looseleaf
- **Bluesky post** — the Bluesky post that shared it, if any
- **Show in Discover** — whether it appears in Discover and aggregated feeds
- **Post settings** — whether it shows recommends, comments and mentions
- **Byline** — who is credited: the contributors on its draft and whoever published it
- **Recommends** — how many readers recommend it
