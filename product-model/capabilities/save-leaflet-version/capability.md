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

# Save a version

Save the Leaflet's current content as a named version.
