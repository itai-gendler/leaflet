---
entities:
- entity: home-leaflet
  shows:
  - Added at
- entity: leaflet
  shows:
  - Title
  - Pages
- entity: post
  shows:
  - Title
  - Published at
- entity: publication
  shows:
  - Name
entryPoints:
- leaflet-web: /home
- leaflet-web: /looseleafs
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/home/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/looseleafs/page.tsx
---

# Home

The signed-in person's Leaflets, drafts and published posts, with the archive.
