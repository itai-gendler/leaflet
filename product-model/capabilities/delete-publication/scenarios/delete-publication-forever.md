---
kind: primary
routes:
  web: Web
steps:
- text: The owner confirms deleting the publication
  kind: actor
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
- text: The Product deletes the publication and its posts from the owner's Bluesky account, deletes its drafts and releases its leaflet.pub address
  kind: product
  actor: user
  entities:
  - entity: publication
    effect: removes
  - entity: post
    effect: removes
    with: publication
  - entity: leaflet
    effect: removes
    from: Publication draft
    with: publication
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/deletePublication.ts
---

# Delete a publication

## Trigger

An owner ends a publication.

## Outcome

The publication, its posts and drafts are gone; its subdomain is free again.
