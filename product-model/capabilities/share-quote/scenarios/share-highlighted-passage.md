---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor highlights a passage and chooses Bluesky or Link
  kind: actor
  actor: visitor
  entities:
  - entity: post
    effect: reads
    facts:
    - Content
  contexts:
    web:
      place: leaflet-web::public::post
- text: The Product gives a link that opens the post scrolled to the highlighted passage
  kind: product
  actor: visitor
  entities:
  - entity: post
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::public::post
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/QuoteHandler.tsx
---

# Share a quote

## Trigger

A reader wants to point others at one passage.

## Outcome

The quote link is copied or put in a Bluesky post; Bluesky posts that link to the post show under its Quotes and notify its author.
