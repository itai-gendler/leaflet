---
appliesTo:
- type: capability
  id: subscribe-by-email
- type: entity
  id: email-subscription
  effect: creates
references:
- kind: code
  role: implementation
  target: src/subscriptions/email.ts
- kind: code
  role: implementation
  target: actions/publications/subscribeEmail.tsx
- kind: code
  role: implementation
  target: app/api/postmark/webhook/route.ts
---

# Readers subscribe by email only while the publication's newsletter is on

With the newsletter off, subscribe forms offer Bluesky instead; an address that reported the newsletter as spam cannot subscribe again from Leaflet.
