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
- kind: code
  role: implementation
  target: src/versioning/restoreVersion.ts
---

# Restore a version

Put a past version's content back into the Leaflet, keeping what it held before as a version.
