---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to copy a version as a new Leaflet
  kind: actor
  actor: user
  entities:
  - entity: leaflet-version
    effect: reads
    facts:
    - Name
    - Snapshot
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet-versions
- text: The Product creates a Leaflet holding the version's content, named after it, on the User's Home
  kind: product
  actor: user
  entities:
  - entity: leaflet
    effect: creates
    to: Draft
    facts:
    - Title
    - Pages
    - Theme
    - Edit link
  - entity: home-leaflet
    effect: creates
    to: On Home
    facts:
    - Added at
    with: leaflet
  - entity: leaflet-version
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet-versions
references:
- kind: code
  role: implementation
  target: actions/versions.ts
- kind: code
  role: implementation
  target: src/versioning/versionAccess.ts
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/actions/VersionHistory.tsx
---

# Copy a version as a new Leaflet

## Trigger

A writer wants to branch from an earlier state.

## Outcome

A new Leaflet with the version's content is on Home; the original and its history are unchanged.
