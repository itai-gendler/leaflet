---
availability:
- place: leaflet-web::public
- place: leaflet-web::signed-in
domain: reader
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/reader/layout.tsx
- kind: code
  role: implementation
  target: actions/reader/getReaderFeed.ts
- kind: code
  role: implementation
  target: actions/reader/getHotFeed.ts
- kind: code
  role: implementation
  target: actions/reader/getNewFeed.ts
---

# Browse the Reader

Read feeds of posts: Trending and New for everyone, and an Inbox of posts from subscribed publications for a signed-in Bluesky account.
