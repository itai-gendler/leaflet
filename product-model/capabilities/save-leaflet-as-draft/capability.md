---
availability:
- place: leaflet-web::signed-in
references:
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/actions/PublishButton.tsx
- kind: code
  role: implementation
  target: actions/publications/moveLeafletToPublication.ts
- kind: code
  role: implementation
  target: src/utils/addDraftToPublication.ts
---

# Save a Leaflet as a publication draft

Move a standalone Leaflet into a publication one owns or contributes to as one of its drafts.
