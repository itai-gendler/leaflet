---
availability:
- place: leaflet-web::signed-in
domain: home
references:
- kind: code
  role: implementation
  target: actions/deleteLeaflet.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/home/LeafletList/LeafletOptions.tsx
---

# Archive a Leaflet

Move a Leaflet from Home into the archive; a publication draft also leaves the publication's drafts.
