---
kind: primary
routes:
  web: Web
steps:
- text: The User enters a domain
  kind: actor
  actor: user
  entities:
  - entity: domain
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::settings
- text: The Product registers it, and its www form redirecting to it, to the User, pending DNS setup
  kind: product
  actor: user
  entities:
  - entity: domain
    effect: creates
    facts:
    - Name
    - Status
    - Assignment
  contexts:
    web:
      place: leaflet-web::signed-in::settings
references:
- kind: code
  role: implementation
  target: actions/domains/index.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/settings/domains/AddDomainForm.tsx
---

# Add a domain

## Trigger

A User wants their own address.

## Outcome

The domain is listed with the DNS records to set.
