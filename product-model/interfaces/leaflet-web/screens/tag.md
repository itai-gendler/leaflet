---
entities:
- entity: tag
  shows:
  - Name
  - Posts
- entity: post
  shows:
  - Title
  - Published at
entryPoints:
- leaflet-web: /tag/:tag
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/tag/[tag]/page.tsx
---

# Tag

The posts filed under one tag.
