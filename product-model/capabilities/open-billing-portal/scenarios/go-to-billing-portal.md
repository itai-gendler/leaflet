---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to manage their plan
  kind: actor
  actor: user
  entities:
  - entity: pro-subscription
    effect: reads
    facts:
    - Plan
    - Period end
  contexts:
    web:
      place: leaflet-web::signed-in::settings
- text: The Product opens the payment provider's billing portal for the User's plan
  kind: product
  actor: user
  entities:
  - entity: payment-provider
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::settings
references:
- kind: code
  role: implementation
  target: actions/createBillingPortalSession.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/settings/ProTab.tsx
---

# Open the billing portal

## Trigger

A Pro User wants to change or cancel their plan.

## Outcome

Changes made there come back through the payment provider.

## Edge cases

- An account that never subscribed has no billing to manage.
