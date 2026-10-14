---
kind: primary
routes:
  web: Web
steps:
- text: A contributor chooses to leave the publication
  kind: actor
  actor: user
  entities:
  - entity: contributor
    effect: reads
    facts:
    - Accepted
  - entity: publication
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
- text: The Product removes them
  kind: product
  actor: user
  entities:
  - entity: contributor
    effect: removes
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

# Leave a publication

## Trigger

A contributor stops writing for a publication.

## Outcome

The publication no longer lists them.
