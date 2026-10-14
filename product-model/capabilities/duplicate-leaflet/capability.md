---
availability:
- place: leaflet-web::signed-in
domain: home
references:
- kind: code
  role: implementation
  target: actions/duplicateLeaflet.ts
- kind: code
  role: implementation
  target: src/utils/copyLeafletContents.ts
---

# Duplicate a Leaflet

Make a copy of a Leaflet from Home; the copy is marked as a copy and added to Home, and a publication draft's copy stays a draft of the same publication.
