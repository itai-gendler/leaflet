---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Remove recommendation in settings and saves
  kind: actor
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Recommended publications
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
- text: The Product removes it
  kind: product
  actor: user
  entities:
  - entity: publication
    effect: changes
    facts:
    - Recommended publications
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
references:
- kind: code
  role: implementation
  target: actions/publications/recommendPublication.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/RecommendedPubsSetting.tsx
---

# Remove a recommendation

## Trigger

An owner no longer recommends a publication.

## Outcome

Readers no longer see it recommended.
