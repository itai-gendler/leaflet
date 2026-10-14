---
appliesTo:
- type: entity
  id: scheduled-post
  effect: removes
permits:
- related:
  - verb: schedules
    entity: publication
  - verb: owns
    entity: user
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

# Schedules are canceled by the publication's owner and contributors, and cleared by the Product on publishing

A schedule ends when a writer cancels it or when the post publishes.
