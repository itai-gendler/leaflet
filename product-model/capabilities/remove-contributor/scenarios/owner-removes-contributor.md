---
kind: primary
routes:
  web: Web
steps:
- text: The owner removes a contributor
  kind: actor
  actor: user
  entities:
  - entity: contributor
    effect: reads
    facts:
    - Accepted
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
- text: The Product removes them and their credit on the publication's drafts
  kind: product
  actor: user
  entities:
  - entity: contributor
    effect: removes
  - entity: publication
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
references:
- kind: code
  role: implementation
  target: actions/publications/contributors.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/ContributorSettings.tsx
---

# Remove a contributor

## Trigger

An owner ends someone's access.

## Outcome

They can no longer write or publish in the publication.
