---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor opens a post's address
  kind: actor
  actor: visitor
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
      place: leaflet-web::public::post
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(published)/p/[didOrHandle]/[rkey]/page.tsx
---

# Read a post

## Trigger

A reader follows a link to a post.

## Outcome

The post is shown in its publication's theme, with its comments, mentions and recommends where shown.

## Edge cases

- A Looseleaf is read under its author's profile on leaflet.pub.
- A deleted or unpublished post's address shows that it is not found.
