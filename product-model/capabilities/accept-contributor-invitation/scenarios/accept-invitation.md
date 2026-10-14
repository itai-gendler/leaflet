---
kind: primary
routes:
  web: Web
steps:
- text: The invited User opens the invitation and accepts
  kind: actor
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Name
    - Logo
  contexts:
    web:
      place: leaflet-web::signed-in::contributor-invitation
- text: The Product makes them a contributor
  kind: product
  actor: user
  entities:
  - entity: contributor
    effect: changes
    facts:
    - Accepted
  contexts:
    web:
      place: leaflet-web::signed-in::contributor-invitation
references:
- kind: code
  role: implementation
  target: actions/publications/contributors.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/ContributorSettings.tsx
---

# Accept an invitation

## Trigger

An invited person decides to join.

## Outcome

The publication's dashboard and drafts open to them.
