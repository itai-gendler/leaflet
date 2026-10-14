---
appliesTo:
- type: entity
  id: scheduled-post
  effect: creates
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

# Posts are scheduled by a publication's owner and accepted contributors while the owner holds Leaflet Pro

Scheduling is a Leaflet Pro feature of the publication's owner; contributors schedule on the owner's plan.
