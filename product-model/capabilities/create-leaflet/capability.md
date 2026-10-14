---
availability:
- place: leaflet-web::public
- place: leaflet-web::signed-in
domain: home
references:
- kind: code
  role: implementation
  target: actions/createNewLeaflet.ts
- kind: code
  role: implementation
  target: src/utils/createLeaflet.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/new/route.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/new-canvas/route.ts
- kind: code
  role: implementation
  target: actions/createNewLeafletFromTemplate.ts
---

# Create a Leaflet

Start a new Leaflet — a document or a canvas — with no account needed, or copy a template Leaflet. A signed-in person's new Leaflet is added to their Home.
