---
availability:
- place: leaflet-web::signed-in
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/[leaflet_id]/publish/PublishPost.tsx
- kind: code
  role: implementation
  target: actions/publishToPublication.ts
- kind: code
  role: implementation
  target: src/utils/publishLeaflet.ts
- kind: code
  role: implementation
  target: actions/publishBskyPost.ts
---

# Publish a post

Publish a Leaflet as a post: as a Looseleaf on one's profile, or to a publication one owns or contributes to. Publishing can share the post on Bluesky, email it to the publication's subscribers and list it in Discover, or do none of these when posted quietly.
