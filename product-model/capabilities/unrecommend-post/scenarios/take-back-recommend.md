---
kind: primary
routes:
  web: Web
steps:
- text: The User removes their recommend
  kind: actor
  actor: user
  entities:
  - entity: recommendation
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::post
- text: The Product deletes the recommend
  kind: product
  actor: user
  entities:
  - entity: recommendation
    effect: removes
  contexts:
    web:
      place: leaflet-web::signed-in::post
references:
- kind: code
  role: implementation
  target: actions/recommendAction.ts
- kind: code
  role: implementation
  target: components/Interactions/RecommendButton.tsx
---

# Remove a recommend

## Trigger

A reader changes their mind.

## Outcome

The post no longer counts their recommend.
