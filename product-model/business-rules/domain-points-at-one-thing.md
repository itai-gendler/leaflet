---
appliesTo:
- type: capability
  id: publish-leaflet-on-domain
- type: capability
  id: assign-domain-to-publication
- type: entity
  id: domain
  facts:
  - Assignment
references:
- kind: code
  role: implementation
  target: actions/domains/index.ts
---

# A domain points at one thing at a time

A domain serves either Leaflets at chosen routes or one publication; pointing it somewhere new clears what it pointed at, and a Leaflet answers at one domain route at a time.
