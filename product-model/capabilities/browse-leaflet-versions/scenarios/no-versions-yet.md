---
kind: edge
routes:
  web: Web
steps:
- text: The User opens Version History when none has been kept
  kind: actor
  actor: user
  entities:
  - entity: leaflet-version
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet-versions
- text: The Product shows that there are no versions yet
  kind: condition
  entities:
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

# No versions yet

## Trigger

The Leaflet was never saved as a version or published.

## Outcome

The history is empty.
