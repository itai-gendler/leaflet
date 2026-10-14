---
kind: primary
routes:
  web: Web
steps:
- text: The User opens the Reader inbox
  kind: actor
  actor: user
  entities:
  - entity: subscription
    effect: reads
    facts: []
  - entity: post
    effect: reads
    facts:
    - Title
    - Description
    - Published at
    - Recommends
  contexts:
    web:
      place: leaflet-web::signed-in::reader-inbox
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/reader/layout.tsx
- kind: code
  role: implementation
  target: actions/reader/getReaderFeed.ts
- kind: code
  role: implementation
  target: actions/reader/getHotFeed.ts
- kind: code
  role: implementation
  target: actions/reader/getNewFeed.ts
---

# Read the Inbox

## Trigger

A signed-in reader catches up.

## Outcome

Posts from the publications they subscribe to are listed newest first.

## Edge cases

- An account without a Bluesky account is sent to Trending instead.
