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

# Copy a version as a new Leaflet

Start a new Leaflet from a past version, leaving the original as it is.
