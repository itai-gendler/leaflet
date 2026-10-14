---
kind: primary
routes:
  hook: Webhook
steps:
- text: The Email delivery service reports that the recipient unsubscribed from inside their email client
  kind: actor
  actor: email-delivery-service
  entities:
  - entity: email-subscription
    effect: reads
    facts:
    - Email
  contexts:
    hook:
      place: email-delivery-webhooks
- text: The Product unsubscribes every subscription at that address
  kind: product
  entities:
  - entity: email-subscription
    effect: changes
    from: Confirmed
    to: Unsubscribed
    facts:
    - Unsubscribed at
  - entity: subscription
    effect: reads
    facts: []
  contexts:
    hook:
      place: email-delivery-webhooks
references:
- kind: code
  role: implementation
  target: app/api/postmark/webhook/route.ts
---

# A one-click unsubscribe from the email client

## Trigger

A reader used their email client's unsubscribe button.

## Outcome

The address receives no more newsletter emails from any Leaflet publication.
