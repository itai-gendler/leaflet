---
entities:
- entity: publication-page
  shows:
  - Title
  - Kind
  - Path
  - Order
  collects:
  - Title
  - Kind
  - Path
  - Order
- entity: publication
  shows:
  - Pages
entryPoints:
- leaflet-web: /lish/:did/:publication/edit
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/edit/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/edit/PublicationPagesEditNav.tsx
---

# Customize publication

Where a publication's home page and navigation pages are written and arranged before publishing them.
