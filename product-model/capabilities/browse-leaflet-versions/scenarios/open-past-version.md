---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Version History
  kind: actor
  actor: user
  entities:
  - entity: leaflet-version
    effect: reads
    facts:
    - Name
    - Kind
    - Saved at
    - Saved by
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet-versions
- text: The User opens one version
  kind: actor
  actor: user
  entities:
  - entity: leaflet-version
    effect: reads
    facts:
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

# Open a past version

## Trigger

A writer wants to see how a Leaflet looked before.

## Outcome

The version's content is shown without changing the Leaflet.

## Edge cases

- A Leaflet with no Leaflet Pro owner has no version history; the panel offers Leaflet Pro instead.
