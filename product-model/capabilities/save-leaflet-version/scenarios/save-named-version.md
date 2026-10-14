---
kind: primary
routes:
  web: Web
steps:
- text: The User names a version and saves it
  kind: actor
  actor: user
  entities:
  - entity: leaflet-version
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet-versions
- text: The Product keeps a copy of the Leaflet's content as a version credited to the User
  kind: product
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Pages
  - entity: leaflet-version
    effect: creates
    facts:
    - Name
    - Kind
    - Saved at
    - Saved by
    - Snapshot
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

# Save a named version

## Trigger

A writer wants to keep the Leaflet as it is now.

## Outcome

The version is listed in the history.

## Edge cases

- Saving when nothing changed since the last version keeps no new version.
