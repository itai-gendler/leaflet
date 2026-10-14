---
domain: leaflet-pro
references:
- kind: code
  role: implementation
  target: stripe/products.ts
- kind: code
  role: implementation
  target: app/api/webhooks/stripe/handle_subscription_updated.ts
- kind: code
  role: implementation
  target: app/api/webhooks/stripe/handle_subscription_deleted.ts
---

# Leaflet Pro subscription

A person's paid Leaflet Pro plan, billed by the payment provider.

## Information kept

- **Plan** — monthly or yearly
- **Period end** — when the paid period ends; Leaflet Pro holds until then

## States

### Active

Paid up and renewing.

### Canceling

Canceled, holding Leaflet Pro until the period ends.

### Past due

A renewal payment failed.

### Canceled

Ended.
