---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the publish date or sharing of a scheduled, paused or failed post
  kind: actor
  actor: user
  entities:
  - entity: scheduled-post
    effect: reads
    facts:
    - Publish at
    - Problem
  - entity: post
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publish
- text: The Product replaces the schedule
  kind: product
  actor: user
  entities:
  - entity: scheduled-post
    effect: changes
    from: Paused
    to: Scheduled
    facts:
    - Publish at
    - Sharing
    - Problem
  contexts:
    web:
      place: leaflet-web::signed-in::publish
references:
- kind: code
  role: implementation
  target: actions/publications/scheduledPosts.ts
- kind: code
  role: implementation
  target: src/scheduledPosts/save.ts
- kind: code
  role: implementation
  target: src/scheduledPosts/eligibility.ts
---

# Reschedule a post

## Trigger

A writer changes when a post goes out, or retries one that did not.

## Outcome

Only the newest schedule publishes the post.

## Edge cases

- A post already publishing can no longer be rescheduled.
