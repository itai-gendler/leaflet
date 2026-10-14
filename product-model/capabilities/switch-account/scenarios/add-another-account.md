---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to add an account and approves the sign-in at another Bluesky account's provider
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in
- text: The Product signs the browser in as the other account, leaving the first account untouched
  kind: product
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Bluesky account
  contexts:
    web:
      place: leaflet-web::signed-in
references:
- kind: code
  role: implementation
  target: app/api/auth/switch-account/route.ts
- kind: code
  role: implementation
  target: actions/savedAccounts.ts
- kind: code
  role: implementation
  target: components/ActionBar/AccountSwitcher.tsx
---

# Add another account

## Trigger

A signed-in User adds a second Bluesky account from the account switcher.

## Outcome

Both accounts are saved in the switcher, and the new one is signed in; neither account is linked or merged into the other.
