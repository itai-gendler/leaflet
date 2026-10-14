---
kind: primary
routes:
  hook: Webhook
steps:
- text: The Payment provider reports the subscription deleted
  kind: actor
  actor: payment-provider
  entities:
  - entity: pro-subscription
    effect: reads
    facts: []
  - entity: subscription
    effect: reads
    facts: []
  contexts:
    hook:
      place: payment-webhooks
- text: The Product marks it canceled; Leaflet Pro lapses at the period end
  kind: product
  actor: payment-provider
  entities:
  - entity: pro-subscription
    effect: changes
    from: Canceling
    to: Canceled
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

# A subscription ends

## Trigger

The subscription ended at the payment provider.

## Outcome

The account loses Leaflet Pro once the paid period is over; scheduled posts and email posts of its publications pause.
