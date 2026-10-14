---
availability:
- place: leaflet-web::public
- place: leaflet-web::signed-in
domain: subscriptions
references:
- kind: code
  role: implementation
  target: actions/publications/subscribeEmail.tsx
- kind: code
  role: implementation
  target: app/api/auth/email-login/route.ts
- kind: code
  role: implementation
  target: src/subscriptions/email.ts
---

# Subscribe by email

Subscribe to a publication's newsletter with an email address, confirmed with a code. A signed-out reader is signed in to the account for that address, created if new. Offered while the publication's newsletter is on.
