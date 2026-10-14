---
kind: primary
routes:
  web: Web
steps:
- text: The User enters an address and chooses Send preview
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: leaflet-web::signed-in::publish
- text: The Product emails the rendered post, marked as a preview, to that address only
  kind: product
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Name
  - entity: post
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publish
references:
- kind: code
  role: implementation
  target: actions/publications/sendPostPreview.tsx
---

# Send a preview

## Trigger

A writer wants to see the email before subscribers do.

## Outcome

The preview arrives; nothing about the post or its sending changes.
