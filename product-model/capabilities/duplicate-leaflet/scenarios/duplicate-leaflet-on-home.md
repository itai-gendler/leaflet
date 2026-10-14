---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Duplicate on a Leaflet on Home
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    as: original
    effect: reads
    facts:
    - Title
  - entity: home-leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::home
- text: The Product creates a copy titled as a copy of the original and adds it to the User's Home
  kind: product
  actor: user
  entities:
  - entity: leaflet
    as: copy
    effect: creates
    to: Draft
    facts:
    - Title
    - Description
    - Pages
    - Theme
    - Edit link
  - entity: home-leaflet
    effect: creates
    to: On Home
    facts:
    - Added at
    with: copy
  contexts:
    web:
      place: leaflet-web::signed-in::home
references:
- kind: code
  role: implementation
  target: actions/duplicateLeaflet.ts
- kind: code
  role: implementation
  target: src/utils/copyLeafletContents.ts
---

# Duplicate a Leaflet

## Trigger

A User wants a copy of a Leaflet to work from.

## Outcome

A new Leaflet with the original's content is on Home; the original is unchanged.

## Edge cases

- Copying a publication draft makes the copy a draft of that publication too, when the User owns or contributes to it.
