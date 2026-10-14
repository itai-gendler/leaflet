---
availability:
- place: payment-webhooks
domain: leaflet-pro
references:
- kind: code
  role: implementation
  target: app/api/webhooks/stripe/route.ts
- kind: code
  role: implementation
  target: app/api/webhooks/stripe/handle_subscription_updated.ts
- kind: code
  role: implementation
  target: app/api/webhooks/stripe/handle_subscription_deleted.ts
- kind: code
  role: implementation
  target: app/api/webhooks/stripe/handle_invoice_payment_failed.ts
---

# Sync a Leaflet Pro subscription

The payment provider reports changes to a Leaflet Pro subscription, and Leaflet updates its status and how long Leaflet Pro holds.
