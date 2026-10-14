---
kind: primary
routes:
  web: Web
steps:
- text: The User picks another account this browser has signed in to
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Profile
  contexts:
    web:
      place: leaflet-web::signed-in
- text: The Product signs the browser in as that account
  kind: product
  actor: user
  entities: []
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

# Switch to another saved account

## Trigger

A User who has signed in to several accounts in this browser picks another one.

## Outcome

The browser is signed in as the chosen account without signing in again.

## Edge cases

- Choosing to log out of the current account while switching ends its session at the same time.
