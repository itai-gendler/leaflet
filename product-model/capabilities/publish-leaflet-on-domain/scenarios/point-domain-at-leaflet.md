---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Publish on a custom domain, picks a domain and a route
  kind: actor
  actor: user
  entities:
  - entity: domain
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product points the domain's route at the Leaflet's view, clearing what the domain or the Leaflet pointed at before
  kind: product
  actor: user
  entities:
  - entity: domain
    effect: changes
    facts:
    - Assignment
    - Route
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
references:
- kind: code
  role: implementation
  target: actions/domains/index.ts
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/actions/ShareOptions/DomainOptions.tsx
---

# Publish a Leaflet on a domain

## Trigger

A writer wants a Leaflet at their own address.

## Outcome

The Leaflet is read at the domain and route; the share menu shows where it is published.
