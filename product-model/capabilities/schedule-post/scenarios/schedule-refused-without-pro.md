---
kind: validation
routes:
  web: Web
steps:
- text: The User tries to schedule in a publication whose owner does not hold Leaflet Pro
  kind: actor
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Pro features
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publish
- text: The Product refuses and points to Leaflet Pro
  kind: condition
  entities:
  - entity: leaflet
    effect: reads
    facts: []
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

# Scheduling without Leaflet Pro is refused

## Trigger

The publication's owner has no Leaflet Pro.

## Outcome

Nothing is scheduled.
