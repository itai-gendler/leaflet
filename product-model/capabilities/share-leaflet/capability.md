---
availability:
- place: leaflet-web::public
- place: leaflet-web::signed-in
references:
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/actions/ShareOptions/index.tsx
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/actions/ShareOptions/getShareLink.ts
---

# Share a Leaflet

Copy a Leaflet's edit link, which lets anyone edit it, or its view link, which only lets people read it; a published Leaflet also offers its post link.
