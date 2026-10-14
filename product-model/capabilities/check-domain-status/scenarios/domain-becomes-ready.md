---
kind: primary
routes:
  web: Web
steps:
- text: The User refreshes a pending domain
  kind: actor
  actor: user
  entities:
  - entity: domain
    effect: reads
    facts:
    - Name
    - Status
  contexts:
    web:
      place: leaflet-web::signed-in::settings
- text: The Product asks the host to verify the domain and shows it ready
  kind: product
  actor: user
  entities:
  - entity: domain
    effect: changes
    facts:
    - Status
  contexts:
    web:
      place: leaflet-web::signed-in::settings
references:
- kind: code
  role: implementation
  target: app/api/rpc/[command]/domain_routes.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/settings/domains/useDomainStatus.ts
---

# A domain's DNS verifies

## Trigger

A User has set the DNS records.

## Outcome

The domain shows as ready.

## Edge cases

- Until the records verify, the domain stays pending with the records still to set.
