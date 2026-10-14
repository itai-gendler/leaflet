---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor chooses to share the view link
  kind: actor
  actor: visitor
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: leaflet-web::public::leaflet
- text: The Product makes the Leaflet's read-only link the first time it is asked for, and copies it
  kind: product
  actor: visitor
  entities:
  - entity: leaflet
    effect: changes
    facts:
    - View link
  contexts:
    web:
      place: leaflet-web::public::leaflet
references:
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/actions/ShareOptions/index.tsx
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/actions/ShareOptions/getShareLink.ts
---

# Copy the view link

## Trigger

A writer wants others to read a Leaflet without editing it.

## Outcome

The read-only link is copied; opening it shows the Leaflet without editing.

## Edge cases

- Copying the edit link copies the link the writer is using; anyone with it can edit.
