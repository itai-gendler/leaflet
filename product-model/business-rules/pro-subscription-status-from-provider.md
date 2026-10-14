---
appliesTo:
- type: entity
  id: pro-subscription
  effect: changes
permits:
- actors:
  - payment-provider
references:
- kind: code
  role: implementation
  target: app/api/webhooks/stripe/handle_subscription_updated.ts
---

# Only the payment provider changes a Leaflet Pro subscription's status

Renewals, cancellations, failed payments and endings arrive from the payment provider; Leaflet Pro holds until the end of the period already paid for.
