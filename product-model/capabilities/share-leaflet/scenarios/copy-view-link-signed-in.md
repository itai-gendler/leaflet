---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to share the view link
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product makes the Leaflet's read-only link the first time it is asked for, and copies it
  kind: product
  actor: user
  entities:
  - entity: leaflet
    effect: changes
    facts:
    - View link
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
references:
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/actions/ShareOptions/index.tsx
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/actions/ShareOptions/getShareLink.ts
---

# Copy the view link while signed in

## Trigger

A writer wants others to read a Leaflet without editing it.

## Outcome

The read-only link is copied; opening it shows the Leaflet without editing.
