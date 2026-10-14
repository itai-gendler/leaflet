---
kind: primary
routes:
  web: Web
steps:
- text: The User opens a post's address
  kind: actor
  actor: user
  entities:
  - entity: post
    effect: reads
    facts:
    - Title
    - Description
    - Tags
    - Cover image
    - Published at
    - Content
    - Byline
    - Recommends
    - Post settings
  contexts:
    web:
      place: leaflet-web::signed-in::post
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(published)/p/[didOrHandle]/[rkey]/page.tsx
---

# Read a post while signed in

## Trigger

A reader follows a link to a post.

## Outcome

The post is shown in its publication's theme, with its comments, mentions and recommends where shown.
