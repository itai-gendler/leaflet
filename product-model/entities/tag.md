---
domain: reader
relations:
- entity: post
  verb: labels
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/tag/[tag]/page.tsx
- kind: code
  role: implementation
  target: actions/searchTags.ts
---

# Tag

A tag writers file posts under; each has a page listing its posts.

## Information kept

- **Name** — the tag, matched without regard to case
- **Posts** — the posts filed under it
