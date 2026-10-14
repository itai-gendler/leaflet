---
availability:
- place: leaflet-web::signed-in
references:
- kind: code
  role: implementation
  target: actions/mergeIdentity.ts
- kind: code
  role: implementation
  target: src/mergeIdentity.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/merge-accounts/page.tsx
---

# Merge accounts

Merge an account that signs in by email only into the Leaflet account of a Bluesky account, keeping everything from both under the Bluesky account.
