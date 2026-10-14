---
availability:
- place: leaflet-web::public
- place: leaflet-web::signed-in
domain: reader
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(published)/p/[didOrHandle]/[rkey]/page.tsx
---

# Read a post

Read a published post at its address, with its publication's theme, its byline, tags, recommends and discussion as its settings allow.
