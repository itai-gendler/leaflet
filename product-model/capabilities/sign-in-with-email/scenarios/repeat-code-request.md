---
kind: edge
routes:
  web: Web
steps:
- text: The Visitor asks for a code again for the same address within a minute
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: leaflet-web::public::sign-in
- text: The Product sends no new email; the code already sent still works
  kind: condition
  entities: []
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

# Asking again within a minute reuses the first code

## Trigger

A second code request for an address arrives less than a minute after the first.

## Outcome

No second email goes out, and the first email's code signs the Visitor in.
