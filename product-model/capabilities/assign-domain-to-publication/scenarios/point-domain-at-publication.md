---
kind: primary
routes:
  web: Web
steps:
- text: The owner picks one of their domains in the publication's Domains settings
  kind: actor
  actor: user
  entities:
  - entity: domain
    effect: reads
    facts:
    - Name
    - Status
  - entity: publication
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
- text: The Product clears the domain's other assignments and points it at the publication
  kind: product
  actor: user
  entities:
  - entity: domain
    effect: changes
    facts:
    - Assignment
  - entity: publication
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
references:
- kind: code
  role: implementation
  target: actions/domains/index.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/PubDomainSettings.tsx
---

# Point a domain at a publication

## Trigger

An owner wants the publication at their own address.

## Outcome

The publication and its posts are read at the domain.
