---
availability:
- place: leaflet-web::signed-in
domain: subscriptions
references:
- kind: code
  role: implementation
  target: actions/publications/subscribeEmail.tsx
- kind: code
  role: implementation
  target: src/subscriptions/unsubscribe.ts
- kind: code
  role: implementation
  target: components/Subscribe/ManageSubscribe.tsx
---

# Unsubscribe from a publication

Stop following a publication: both the Bluesky subscription and any email subscription end.
