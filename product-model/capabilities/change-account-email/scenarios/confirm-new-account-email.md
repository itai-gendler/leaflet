---
kind: primary
routes:
  web: Web
steps:
- text: The User enters a new email address
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Email
  contexts:
    web:
      place: leaflet-web::signed-in::settings
- text: The Product emails a confirmation code to the new address
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::settings
- text: The User enters the code
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::settings
- text: The Product sets the address as the account's email and moves the account's email subscriptions and billing contact to it
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - Email
  - entity: email-subscription
    effect: changes
    facts:
    - Email
  - entity: subscription
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::settings
references:
- kind: code
  role: implementation
  target: actions/emailAuth.tsx
- kind: code
  role: implementation
  target: components/AccountEmailForm.tsx
---

# Change the account email

## Trigger

A User wants a different email on their account.

## Outcome

The account signs in and receives subscription emails at the new address.
