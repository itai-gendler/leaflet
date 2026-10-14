---
kind: primary
routes:
  hook: Webhook
steps:
- text: The Payment provider reports a renewed or changed subscription
  kind: actor
  actor: payment-provider
  entities:
  - entity: pro-subscription
    effect: reads
    facts:
    - Plan
  - entity: subscription
    effect: reads
    facts: []
  contexts:
    hook:
      place: payment-webhooks
- text: The Product updates the plan and period end and extends Leaflet Pro to the new period end
  kind: product
  actor: payment-provider
  entities:
  - entity: pro-subscription
    effect: changes
    from: Past due
    to: Active
    facts:
    - Plan
    - Period end
  - entity: user
    effect: changes
    facts:
    - Leaflet Pro
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

# A subscription renews or changes

## Trigger

A renewal or plan change happens at the payment provider.

## Outcome

Leaflet Pro holds until the new period end.
