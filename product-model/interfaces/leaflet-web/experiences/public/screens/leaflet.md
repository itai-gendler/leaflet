---
entities:
- entity: leaflet
  shows:
  - Title
  - Pages
  - Theme
- entity: page
  shows:
  - Kind
  - Blocks
- entity: block
  shows:
  - Type
  - Content
  - Position
  - Poll options
  collects:
  - Content
  - Poll options
- entity: poll-vote
  collects:
  - Options
entryPoints:
- leaflet-web: /:leafletId
references:
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/Leaflet.tsx
---

# Leaflet

A Leaflet opened by its edit link without signing in: its pages side by side, to write in, rearrange, theme, share and vote in. Opened by its view link, the same Leaflet is read-only.
