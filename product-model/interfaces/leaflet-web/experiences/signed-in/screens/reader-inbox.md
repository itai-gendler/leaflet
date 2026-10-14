---
entities:
- entity: post
  shows:
  - Title
  - Description
  - Published at
  - Recommends
- entity: subscription
  shows:
  - Subscribed at
entryPoints:
- leaflet-web: /reader
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/reader/page.tsx
---

# Reader inbox

Posts from the publications the signed-in reader subscribes to.
