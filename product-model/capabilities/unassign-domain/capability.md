---
availability:
- place: leaflet-web::signed-in
domain: domains
references:
- kind: code
  role: implementation
  target: actions/domains/index.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/settings/domains/UnassignButton.tsx
---

# Unassign a domain

Stop a domain pointing at its Leaflets or publication, keeping it registered.
