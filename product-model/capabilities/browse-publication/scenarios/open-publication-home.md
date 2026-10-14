---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor opens a publication's address
  kind: actor
  actor: visitor
  entities:
  - entity: publication
    effect: reads
    facts:
    - Name
    - Description
    - Logo
    - Theme
    - Pages
    - Recommended publications
  - entity: post
    effect: reads
    facts:
    - Title
    - Description
    - Published at
  contexts:
    web:
      place: leaflet-web::public::publication
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/archive/page.tsx
---

# Open a publication

## Trigger

A reader visits a publication.

## Outcome

Its home page, navigation and posts are shown, newest first in the archive.

## Edge cases

- Posts hidden from Discover still appear in their own publication.
