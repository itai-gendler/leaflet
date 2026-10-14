---
appliesTo:
- type: capability
  id: save-leaflet-version
- type: capability
  id: restore-leaflet-version
- type: capability
  id: copy-leaflet-version
- type: entity
  id: leaflet-version
references:
- kind: code
  role: implementation
  target: actions/versions.ts
- kind: code
  role: implementation
  target: src/versioning/versionAccess.ts
- kind: code
  role: implementation
  target: src/versioning/cutPublishVersion.ts
---

# Saving, restoring and copying versions are Leaflet Pro features

A Leaflet whose owner holds Leaflet Pro keeps a version history every writer of it can browse; only writers holding Leaflet Pro save, restore or copy versions. Publishing such a Leaflet keeps a version of what was published.
