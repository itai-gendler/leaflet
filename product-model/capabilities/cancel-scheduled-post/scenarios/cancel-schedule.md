---
kind: primary
routes:
  web: Web
steps:
- text: The User cancels a scheduled post
  kind: actor
  actor: user
  entities:
  - entity: scheduled-post
    effect: reads
    facts:
    - Publish at
  - entity: post
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
- text: The Product drops the schedule; the draft stays
  kind: product
  actor: user
  entities:
  - entity: scheduled-post
    effect: removes
    from: Scheduled
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
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

# Cancel a schedule

## Trigger

A writer no longer wants the post to go out on schedule.

## Outcome

The draft is an ordinary draft again.

## Edge cases

- A post that has started publishing cannot be canceled; the writer is told it is going out.
