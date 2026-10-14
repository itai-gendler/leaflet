---
availability:
- place: leaflet-web::public
- place: leaflet-web::signed-in
domain: subscriptions
references:
- kind: code
  role: implementation
  target: actions/publications/subscribeToPublication.ts
- kind: code
  role: implementation
  target: src/subscriptions/atproto.ts
- kind: code
  role: implementation
  target: components/Subscribe/HandleSubscribe.tsx
---

# Subscribe with Bluesky

Subscribe to a publication with one's Bluesky account; someone signed out signs in with Bluesky on the way. The publication's owner is notified.
