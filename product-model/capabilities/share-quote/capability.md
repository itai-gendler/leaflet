---
availability:
- place: leaflet-web::public
- place: leaflet-web::signed-in
domain: reader
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/QuoteHandler.tsx
---

# Share a quote

Highlight a passage of a post and share a link to exactly that passage, on Bluesky or by copying it.
