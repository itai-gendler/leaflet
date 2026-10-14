---
kind: primary
routes:
  hook: Webhook
steps:
- text: The Email delivery service reports a hard bounce or spam complaint for a newsletter email
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
- text: The Product unsubscribes that subscription
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

# A hard bounce or spam complaint unsubscribes the address

## Trigger

An email could not be delivered for good, or was reported as spam.

## Outcome

The address receives no more emails from that publication.

## Edge cases

- A soft bounce is noted and the address stays subscribed.
