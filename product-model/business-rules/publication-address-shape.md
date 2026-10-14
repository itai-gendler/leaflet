---
appliesTo:
- type: capability
  id: create-publication
- type: entity
  id: publication
  facts:
  - Address
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/createPub/createPublication.ts
---

# A publication's address is a leaflet.pub subdomain of 3 to 63 lowercase letters, digits and hyphens

The subdomain chosen at creation becomes the publication's default address, served at once.
