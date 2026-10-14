---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor follows the unsubscribe link in a newsletter email
  kind: actor
  actor: visitor
  entities:
  - entity: email-subscription
    effect: reads
    facts:
    - Email
  contexts:
    web:
      place: leaflet-web::public::unsubscribe
- text: The Product unsubscribes the address and, for a linked account, deletes its Bluesky subscription too
  kind: product
  entities:
  - entity: email-subscription
    effect: changes
    from: Confirmed
    to: Unsubscribed
    facts:
    - Unsubscribed at
  - entity: subscription
    effect: removes
  contexts:
    web:
      place: leaflet-web::public::unsubscribe
references:
- kind: code
  role: implementation
  target: app/emails/unsubscribe/route.ts
- kind: code
  role: implementation
  target: src/subscriptions/unsubscribe.ts
---

# Unsubscribe from an email

## Trigger

A subscriber no longer wants the emails.

## Outcome

The page confirms the address is unsubscribed and links to managing subscriptions.

## Edge cases

- Following the link again changes nothing.
- An unknown link shows that it is invalid.
