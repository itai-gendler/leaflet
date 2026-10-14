---
availability:
- place: leaflet-web::public
- place: leaflet-web::signed-in
domain: reader
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/p/[didOrHandle]/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/p/[didOrHandle]/layout.tsx
---

# View a profile

See a person's profile: their posts, comments and subscriptions.
