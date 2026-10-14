---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a domain
  kind: actor
  actor: user
  entities:
  - entity: domain
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: leaflet-web::signed-in::settings
- text: The Product clears its assignments and removes it and its www form
  kind: product
  actor: user
  entities:
  - entity: domain
    effect: removes
  contexts:
    web:
      place: leaflet-web::signed-in::settings
references:
- kind: code
  role: implementation
  target: actions/domains/index.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/settings/domains/DeleteDomainButton.tsx
---

# Delete a domain

## Trigger

A User no longer uses a domain with Leaflet.

## Outcome

The domain no longer serves anything from Leaflet.
