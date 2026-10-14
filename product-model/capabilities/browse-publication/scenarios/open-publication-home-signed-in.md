---
kind: primary
routes:
  web: Web
steps:
- text: The User opens a publication's address
  kind: actor
  actor: user
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
      place: leaflet-web::signed-in::publication
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/archive/page.tsx
---

# Open a publication while signed in

## Trigger

A reader visits a publication.

## Outcome

Its home page, navigation and posts are shown, newest first in the archive.
