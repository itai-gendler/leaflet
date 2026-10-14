---
kind: primary
routes:
  web: Web
steps:
- text: The User picks monthly or yearly and goes to checkout
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Leaflet Pro
  contexts:
    web:
      place: leaflet-web::signed-in::upgrade
- text: The User pays at the payment provider's checkout, optionally with a promotion code
  kind: actor
  actor: user
  entities:
  - entity: payment-provider
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::upgrade
- text: The Product records the subscription and gives the account Leaflet Pro until the period ends
  kind: product
  actor: user
  entities:
  - entity: pro-subscription
    effect: creates
    to: Active
    facts:
    - Plan
    - Period end
  - entity: user
    effect: changes
    facts:
    - Leaflet Pro
  - entity: subscription
    effect: reads
    facts: []
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::upgrade
references:
- kind: code
  role: implementation
  target: actions/createCheckoutSession.ts
- kind: code
  role: implementation
  target: app/api/checkout/success/route.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/upgrade/page.tsx
- kind: code
  role: implementation
  target: stripe/products.ts
---

# Buy Leaflet Pro

## Trigger

A User wants analytics, newsletters, scheduling, group publications or version history.

## Outcome

The account holds Leaflet Pro right away and returns to where it started.

## Edge cases

- An account that already holds Leaflet Pro is told so instead of checking out again.
- Leaving checkout returns to where the User started, with nothing bought.
