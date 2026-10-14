---
appliesTo:
- type: capability-scenario
  id: publish-quietly
- type: entity
  id: post
  facts:
  - Show in Discover
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/[leaflet_id]/publish/PublishPost.tsx
- kind: code
  role: implementation
  target: src/utils/publishLeaflet.ts
---

# A quietly posted post is not shared, emailed or listed in Discover

Posting quietly turns off every share; updating a quiet post later keeps it out of Discover.
