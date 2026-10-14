---
kind: validation
routes:
  web: Web
steps:
- text: The User confirms an address that another account with a Bluesky account already uses
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::settings
- text: The Product refuses the change
  kind: condition
  entities:
  - entity: user
    effect: reads
    facts:
    - Email
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

# The address belongs to another account

## Trigger

The new address already belongs to another account that the Product will not merge.

## Outcome

The account's email is unchanged.

## Edge cases

- When the address belongs to an email-only account and this account has a Bluesky account, the two accounts are merged instead.
