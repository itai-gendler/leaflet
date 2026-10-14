---
type: webhook
actors:
- payment-provider
references:
- kind: code
  role: implementation
  target: app/api/webhooks/stripe/route.ts
---

# Payment webhooks

The signed endpoint Stripe calls when a Leaflet Pro checkout completes and when a subscription is created, renewed, changed, canceled or fails to collect payment.
