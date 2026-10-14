---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Delete on a navigation entry and confirms
  kind: actor
  actor: user
  entities:
  - entity: publication-page
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: leaflet-web::signed-in::publication-pages
- text: The Product removes it from the draft navigation
  kind: product
  actor: user
  entities:
  - entity: publication-page
    effect: removes
  contexts:
    web:
      place: leaflet-web::signed-in::publication-pages
references:
- kind: code
  role: implementation
  target: src/replicache/mutations.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/edit/PublicationPagesEditNav.tsx
---

# Delete a navigation page

## Trigger

An owner drops a page.

## Outcome

The entry is gone from the draft; readers lose it once the pages are published.
