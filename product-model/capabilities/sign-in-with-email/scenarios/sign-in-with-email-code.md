---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor enters their email address
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: leaflet-web::public::sign-in
- text: The Product emails a sign-in code to the address
  kind: product
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::public::sign-in
- text: The Visitor enters the code from the email
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: leaflet-web::public::sign-in
- text: The Product signs in the User with that email, creating the account when the address is new
  kind: product
  entities:
  - entity: user
    effect: creates
    facts:
    - Email
  contexts:
    web:
      place: leaflet-web::public::sign-in
references:
- kind: code
  role: implementation
  target: actions/emailAuth.tsx
- kind: code
  role: implementation
  target: app/login/confirm/page.tsx
- kind: code
  role: implementation
  target: actions/login.ts
---

# Sign in with a code sent by email

## Trigger

A Visitor chooses to log in with their email.

## Outcome

The Visitor is signed in to the account for that email, which exists from now on.

## Edge cases

- Leaflets the Visitor kept on Home in this browser while signed out are added to the account's Home.
- Votes cast in polls from this browser are carried over to the account.
- Email subscriptions made with this address before the account existed are linked to it.
