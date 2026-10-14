---
kind: primary
routes:
  web: Web
steps:
- text: The owner publishes the customized publication
  kind: actor
  actor: user
  entities:
  - entity: publication-page
    effect: reads
    facts:
    - Title
    - Path
    - Order
  - entity: publication
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-pages
- text: The Product writes each page to the owner's Bluesky account, replaces the navigation and applies the theme
  kind: product
  actor: user
  entities:
  - entity: publication
    effect: changes
    facts:
    - Pages
    - Theme
  - entity: page
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-pages
references:
- kind: code
  role: implementation
  target: actions/publishPublicationPages.ts
- kind: code
  role: implementation
  target: src/utils/publishPublicationPages.ts
---

# Publish the customized pages

## Trigger

An owner is happy with the customized pages.

## Outcome

Readers see the new home page, pages and navigation.
