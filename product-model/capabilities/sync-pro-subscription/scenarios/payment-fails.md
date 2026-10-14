---
kind: edge
routes:
  hook: Webhook
steps:
- text: The Payment provider reports a failed payment
  kind: actor
  actor: payment-provider
  entities:
  - entity: pro-subscription
    effect: reads
    facts: []
  contexts:
    hook:
      place: payment-webhooks
- text: The Product marks the subscription past due
  kind: product
  actor: payment-provider
  entities:
  - entity: pro-subscription
    effect: changes
    from: Active
    to: Past due
    facts: []
  - entity: subscription
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

# A renewal payment fails

## Trigger

A renewal could not be collected.

## Outcome

The subscription shows past due; Leaflet Pro holds until the period already paid for ends.
