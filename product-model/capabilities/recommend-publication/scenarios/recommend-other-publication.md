---
kind: primary
routes:
  web: Web
steps:
- text: The User picks one of their publications to recommend the publication they are reading
  kind: actor
  actor: user
  entities:
  - entity: publication
    as: recommended
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: leaflet-web::signed-in::publication
- text: The Product adds it to that publication's recommendations
  kind: product
  actor: user
  entities:
  - entity: publication
    as: recommender
    effect: changes
    facts:
    - Recommended publications
  contexts:
    web:
      place: leaflet-web::signed-in::publication
references:
- kind: code
  role: implementation
  target: actions/publications/recommendPublication.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/RecommendedPubsSetting.tsx
---

# Recommend a publication

## Trigger

An owner wants their readers to find a publication they like.

## Outcome

Readers of the owner's publication see the recommendation.
