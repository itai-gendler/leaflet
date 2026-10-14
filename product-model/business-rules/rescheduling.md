---
appliesTo:
- type: entity
  id: scheduled-post
  effect: changes
permits:
- related:
  - verb: schedules
    entity: publication
  - verb: owns
    entity: user
  when:
  - entity: publication
    fact: Pro features
    is: true
- related:
  - verb: schedules
    entity: publication
  - verb: has
    entity: contributor
  - verb: holds
    entity: user
  when:
  - entity: contributor
    fact: Accepted
    is: true
  - entity: publication
    fact: Pro features
    is: true
- unattended: true
references:
- kind: code
  role: implementation
  target: src/scheduledPosts/save.ts
- kind: code
  role: implementation
  target: src/scheduledPosts/eligibility.ts
- kind: code
  role: implementation
  target: app/api/inngest/functions/publish_scheduled_post.ts
---

# Scheduled posts are rescheduled by the publication's owner and contributors with Leaflet Pro, and paused or failed by the Product

Writers change a schedule while the owner holds Leaflet Pro; the Product itself marks a post paused or failed when its time comes.
