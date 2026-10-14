---
entities:
- entity: publication
  collects:
  - Name
  - Description
  - Logo
  - Address
entryPoints:
- leaflet-web: /lish/createPub
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/createPub/page.tsx
---

# New publication

Where a person names and creates a publication.
