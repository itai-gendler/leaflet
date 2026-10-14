---
kind: primary
routes:
  hook: Webhook
steps:
- text: The Payment provider reports a subscription set to end at the period end
  kind: actor
  actor: payment-provider
  entities:
  - entity: pro-subscription
    effect: reads
    facts:
    - Period end
  - entity: subscription
    effect: reads
    facts: []
  contexts:
    hook:
      place: payment-webhooks
- text: The Product marks it canceling; Leaflet Pro holds until the period end
  kind: product
  actor: payment-provider
  entities:
  - entity: pro-subscription
    effect: changes
    from: Active
    to: Canceling
    facts: []
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    hook:
      place: payment-webhooks
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

# A subscription is set to cancel

## Trigger

The subscriber canceled in the billing portal.

## Outcome

Leaflet Pro keeps working until the paid period ends.
