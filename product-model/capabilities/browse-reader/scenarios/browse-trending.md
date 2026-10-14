---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor opens the Reader's Trending or New feed
  kind: actor
  actor: visitor
  entities:
  - entity: post
    effect: reads
    facts:
    - Title
    - Description
    - Published at
    - Recommends
  contexts:
    web:
      place: leaflet-web::discover
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/reader/layout.tsx
- kind: code
  role: implementation
  target: actions/reader/getReaderFeed.ts
- kind: code
  role: implementation
  target: actions/reader/getHotFeed.ts
- kind: code
  role: implementation
  target: actions/reader/getNewFeed.ts
---

# Browse Trending and New

## Trigger

Someone wants something to read.

## Outcome

Recent and popular posts listed in Discover are shown; posts hidden from Discover are not.
