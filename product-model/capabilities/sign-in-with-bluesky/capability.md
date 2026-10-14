---
availability:
- place: leaflet-web::public
references:
- kind: code
  role: implementation
  target: app/api/oauth/[route]/route.ts
- kind: code
  role: implementation
  target: src/auth.ts
---

# Sign in with Bluesky

Sign in by authorizing Leaflet at one's Bluesky account provider. A Bluesky account Leaflet has not seen gets a new Leaflet account; the person returns to the page they started from.
