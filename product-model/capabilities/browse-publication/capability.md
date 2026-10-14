---
availability:
- place: leaflet-web::public
- place: leaflet-web::signed-in
domain: reader
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/archive/page.tsx
---

# Browse a publication

Read a publication's home page, its pages and its archive of posts at its address.
