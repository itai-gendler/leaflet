---
entities:
- entity: user
  shows:
  - Profile
  - Bluesky account
- entity: post
  shows:
  - Title
  - Published at
entryPoints:
- leaflet-web: /p/:handle
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/p/[didOrHandle]/layout.tsx
---

# Profile

A person's public profile: their posts, comments and subscriptions.
