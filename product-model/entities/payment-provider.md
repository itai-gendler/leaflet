---
kind: system
acts: external
references:
- kind: code
  role: implementation
  target: app/api/webhooks/stripe/route.ts
---

# Payment provider

Stripe, which runs Leaflet Pro checkout and billing and tells Leaflet through signed webhooks when a subscription starts, renews, changes, fails to collect payment or ends.
