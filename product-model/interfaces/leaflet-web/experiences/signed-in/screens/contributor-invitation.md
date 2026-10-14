---
entities:
- entity: publication
  shows:
  - Name
  - Logo
- entity: contributor
  shows:
  - Accepted
entryPoints:
- leaflet-web: /lish/:did/:publication/contributor_accept
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/contributor_accept/AcceptContent.tsx
---

# Contributor invitation

Where an invited person accepts an invitation to write for a publication.
