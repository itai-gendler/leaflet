---
availability:
- place: leaflet-web::signed-in
domain: version-history
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

# Browse a Leaflet's versions

See a Leaflet's version history and open a past version. The history exists for Leaflets of a Leaflet Pro account, and every writer of such a Leaflet sees it.
