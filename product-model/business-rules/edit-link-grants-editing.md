---
appliesTo:
- type: entity
  id: leaflet
- type: entity
  id: page
- type: entity
  id: block
references:
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/actions/ShareOptions/getShareLink.ts
- kind: code
  role: implementation
  target: drizzle/schema.ts
---

# Anyone with a Leaflet's edit link edits it; its view link only shows it

A Leaflet's edit link is its key: whoever holds it writes in it, signed in or not. Its view link opens the same Leaflet read-only. Neither link names a person.

## Rationale

Leaflets are made and shared without accounts, so access travels with the link rather than with a person.
