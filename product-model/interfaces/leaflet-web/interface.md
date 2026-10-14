---
type: web
actors:
- visitor
- user
entryPoints:
- web: /
- web: /new
- web: /home
- web: /reader
references:
- kind: code
  role: implementation
  target: middleware.ts
- kind: code
  role: implementation
  target: app/layout.tsx
- kind: code
  role: implementation
  target: app/(app)/(identity)/layout.tsx
---

# Leaflet web app

The Leaflet web app at leaflet.pub, including every publication's pages served on its leaflet.pub subdomain or a custom domain, and the links Leaflet's emails open. Anyone reaches Leaflets by their links, published posts, publication pages, profiles, tag pages and the public Reader feeds; Home, the Reader inbox, notifications, settings and publication dashboards need a signed-in account.
