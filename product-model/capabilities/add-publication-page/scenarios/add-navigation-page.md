---
kind: primary
routes:
  web: Web
steps:
- text: The owner adds a navigation entry with a title and path, or an external link
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-pages
- text: The Product adds the entry to the publication's draft navigation
  kind: product
  actor: user
  entities:
  - entity: publication-page
    effect: creates
    facts:
    - Title
    - Kind
    - Path
    - Order
  - entity: publication
    effect: reads
    facts: []
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

# Add a page to the navigation

## Trigger

An owner wants an About page or a link in the publication's navigation.

## Outcome

The page is in the draft navigation, ready to write; readers see it once published.

## Edge cases

- A page path is a single lowercase segment; the home page is the root.
