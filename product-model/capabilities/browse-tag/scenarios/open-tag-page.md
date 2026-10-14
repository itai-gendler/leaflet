---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor opens a tag
  kind: actor
  actor: visitor
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
    - Posts
  - entity: post
    effect: reads
    facts:
    - Title
    - Published at
  contexts:
    web:
      place: leaflet-web::tag
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/tag/[tag]/page.tsx
---

# Open a tag

## Trigger

A reader follows a tag.

## Outcome

Posts with that tag, from every publication, are listed.
