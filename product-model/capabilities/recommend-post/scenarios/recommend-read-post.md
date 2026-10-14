---
kind: primary
routes:
  web: Web
steps:
- text: The User recommends a post
  kind: actor
  actor: user
  entities:
  - entity: post
    effect: reads
    facts:
    - Recommends
  contexts:
    web:
      place: leaflet-web::signed-in::post
- text: The Product records the recommend in the User's Bluesky account and notifies the author
  kind: product
  actor: user
  entities:
  - entity: recommendation
    effect: creates
    facts:
    - Recommended at
  - entity: notification
    effect: creates
    to: Unread
    facts:
    - Kind
    - Subject
    - Created at
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

# Recommend a post

## Trigger

A reader liked a post.

## Outcome

The post's recommend count rises and the author sees a notification.

## Edge cases

- Recommending a post already recommended changes nothing.
