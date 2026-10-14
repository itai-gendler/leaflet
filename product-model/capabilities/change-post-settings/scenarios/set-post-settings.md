---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Settings for this post and turns options on or off
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Post settings
  - entity: post
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product keeps the choices on the draft, and they apply when it is published or updated
  kind: product
  actor: user
  entities:
  - entity: leaflet
    effect: changes
    facts:
    - Post settings
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
references:
- kind: code
  role: implementation
  target: components/PostSettings.tsx
- kind: code
  role: implementation
  target: src/replicache/mutations.ts
---

# Change a post's settings

## Trigger

A writer wants one post to behave differently from the publication's defaults.

## Outcome

The post's settings are saved with its draft.
