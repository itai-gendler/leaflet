---
entities:
- entity: leaflet-version
  shows:
  - Name
  - Kind
  - Saved at
  - Saved by
  - Snapshot
  collects:
  - Name
- entity: leaflet
  shows:
  - Title
entryPoints:
- leaflet-web: /:leafletId/versions/:versionId
references:
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/actions/VersionHistory.tsx
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/versions/[version_id]/page.tsx
---

# Version history

A Leaflet's version history and one version opened from it.
