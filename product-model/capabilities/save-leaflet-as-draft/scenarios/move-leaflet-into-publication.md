---
kind: primary
routes:
  web: Web
steps:
- text: The User picks a publication under Publish to… and chooses Save as Draft
  kind: actor
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Name
  - entity: leaflet
    effect: reads
    facts:
    - Title
    - Description
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product makes the Leaflet a draft of the publication with its title and description, adding a post title block
  kind: product
  actor: user
  entities:
  - entity: leaflet
    effect: changes
    from: Draft
    to: Publication draft
    facts:
    - Title
    - Description
  - entity: block
    effect: creates
    facts:
    - Type
    - Position
  - entity: publication
    effect: reads
    facts: []
  - entity: post
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
references:
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/actions/PublishButton.tsx
- kind: code
  role: implementation
  target: actions/publications/moveLeafletToPublication.ts
- kind: code
  role: implementation
  target: src/utils/addDraftToPublication.ts
---

# Save as a draft of a publication

## Trigger

A writer decides a Leaflet belongs in a publication.

## Outcome

The Leaflet is listed among the publication's drafts.
