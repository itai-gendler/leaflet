---
relations:
- entity: page
  verb: has
  cardinality: one-to-many
- entity: leaflet-version
  verb: keeps
  cardinality: one-to-many
- entity: leaflet-comment
  verb: carries
  cardinality: one-to-many
- entity: post
  verb: is published as
  cardinality: one-to-one
- entity: scheduled-post
  verb: is scheduled as
  cardinality: one-to-one
- entity: email-post
  verb: is sent as
  cardinality: one-to-one
- entity: home-leaflet
  verb: appears as
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/utils/createLeaflet.ts
- kind: code
  role: implementation
  target: actions/createNewLeaflet.ts
- kind: code
  role: implementation
  target: drizzle/schema.ts
---

# Leaflet

A collaborative document: one or more pages of blocks, shared by its edit link and, once someone asks for it, a read-only view link. A Leaflet may stand alone, be a draft of a publication, or be the draft behind a published post, which it keeps so the post can be updated.

## Information kept

- **Title** — the text of its first heading, or the title given when publishing
- **Description** — the short description given when publishing
- **Pages** — its pages in order; the first is the one it opens on
- **Theme** — its page and background colors, background image, accent and text colors, fonts, page width and whether the Leaflet watermark shows
- **Edit link** — the private link that opens it for editing
- **View link** — the read-only link to it, made the first time someone shares it
- **Post settings** — the per-post choices to show the post in Discover and to show its recommends, comments and mentions
- **Archived in publication** — whether a publication draft is archived out of the dashboard's drafts
- **Pro owner** — whether someone holding Leaflet Pro keeps it on Home or owns its publication, which gives it a version history

## States

### Draft

A standalone Leaflet that is not published.

### Publication draft

A draft held by a publication, written by its owner and contributors.

### Published

Published as a post; editing it changes the draft until the post is updated.
