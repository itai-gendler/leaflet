---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to restore a version
  kind: actor
  actor: user
  entities:
  - entity: leaflet-version
    as: restored
    effect: reads
    facts:
    - Snapshot
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet-versions
- text: The Product keeps the current content as a version, then replaces the Leaflet's content with the restored version's
  kind: product
  actor: user
  entities:
  - entity: leaflet-version
    as: before-restore
    effect: creates
    facts:
    - Kind
    - Saved at
    - Saved by
    - Snapshot
  - entity: leaflet
    effect: changes
    facts:
    - Pages
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
- kind: code
  role: implementation
  target: src/versioning/restoreVersion.ts
---

# Restore a past version

## Trigger

A writer wants an earlier state back.

## Outcome

The Leaflet shows the restored content for everyone, and its previous content stays in the history.
