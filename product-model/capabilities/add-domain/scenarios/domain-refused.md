---
kind: validation
routes:
  web: Web
steps:
- text: The User enters an invalid domain, one already in use, or a reserved name
  kind: actor
  actor: user
  entities:
  - entity: domain
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::settings
- text: The Product refuses and adds nothing
  kind: condition
  entities: []
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

# A domain that cannot be added

## Trigger

The domain is unusable for this account.

## Outcome

No domain is added.
