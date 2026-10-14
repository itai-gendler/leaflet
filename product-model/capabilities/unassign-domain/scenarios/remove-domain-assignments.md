---
kind: primary
routes:
  web: Web
steps:
- text: The User unassigns a domain
  kind: actor
  actor: user
  entities:
  - entity: domain
    effect: reads
    facts:
    - Assignment
  contexts:
    web:
      place: leaflet-web::signed-in::settings
- text: The Product removes everything the domain points at
  kind: product
  actor: user
  entities:
  - entity: domain
    effect: changes
    facts:
    - Assignment
    - Route
  contexts:
    web:
      place: leaflet-web::signed-in::settings
references:
- kind: code
  role: implementation
  target: actions/domains/index.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/settings/domains/UnassignButton.tsx
---

# Unassign a domain

## Trigger

A User frees a domain for something else.

## Outcome

The domain stays registered, pointing nowhere.
