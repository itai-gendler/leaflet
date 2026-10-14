---
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
  target: src/versioning/cutPublishVersion.ts
---

# Version

A saved copy of a Leaflet's content at one moment, kept in its version history.

## Information kept

- **Name** — an optional name given when saving
- **Kind** — saved by a writer, made automatically when the Leaflet is published or updated, or kept automatically just before a restore
- **Saved at** — when it was made
- **Saved by** — who saved it
- **Snapshot** — the Leaflet's content as it was
