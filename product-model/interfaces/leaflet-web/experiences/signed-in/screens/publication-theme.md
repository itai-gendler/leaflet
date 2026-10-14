---
entities:
- entity: publication
  shows:
  - Theme
  collects:
  - Theme
entryPoints:
- leaflet-web: /lish/:did/:publication/theme-settings
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/theme-settings/page.tsx
---

# Publication theme

Where a publication's theme is set, with previews of its home page and a post.
