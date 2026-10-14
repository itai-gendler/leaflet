---
entities:
- entity: post
  shows:
  - Title
  - Description
  - Published at
  - Recommends
entryPoints:
- leaflet-web: /reader/trending
- leaflet-web: /reader/new
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/reader/trending/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/reader/new/page.tsx
---

# Reader: Trending and New

The Reader's public feeds of posts listed in Discover.
