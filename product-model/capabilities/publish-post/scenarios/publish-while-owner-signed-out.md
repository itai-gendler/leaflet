---
kind: edge
routes:
  web: Web
steps:
- text: The User publishes a publication draft while the owner's Bluesky sign-in has expired
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Title
  - entity: publication
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publish
- text: The Product publishes nothing and says the owner needs to sign in again
  kind: condition
  entities:
  - entity: publication
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: leaflet-web::signed-in::publish
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/[leaflet_id]/publish/PublishPost.tsx
- kind: code
  role: implementation
  target: actions/publishToPublication.ts
- kind: code
  role: implementation
  target: src/utils/publishLeaflet.ts
- kind: code
  role: implementation
  target: actions/publishBskyPost.ts
- kind: code
  role: implementation
  target: src/atproto-oauth.ts
---

# The publication owner's Bluesky session has expired

## Trigger

Leaflet cannot act for the owner's Bluesky account.

## Outcome

The draft is unchanged and still unpublished.

## Edge cases

- A second publish of the same draft while one is running is refused until the first finishes.
- When the Bluesky account's server refuses the post, the writer is told and nothing is left half-published.
