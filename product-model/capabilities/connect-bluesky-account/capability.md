---
availability:
- place: leaflet-web::signed-in
references:
- kind: code
  role: implementation
  target: app/api/oauth/[route]/route.ts
- kind: code
  role: implementation
  target: src/subscriptions/atproto.ts
---

# Connect a Bluesky account

Connect a Bluesky account to an account that signs in by email only, so the account can publish and subscribe with Bluesky.
