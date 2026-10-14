---
kind: primary
routes:
  web: Web
steps:
- text: The User publishes a draft of a publication they own or contribute to, with sharing on Bluesky and email on
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Title
    - Description
    - Post settings
  - entity: publication
    effect: reads
    facts:
    - Name
    - Newsletter
  contexts:
    web:
      place: leaflet-web::signed-in::publish
- text: The Product writes the post to the publication owner's Bluesky account under the publication, crediting the draft's contributors and the publisher in its byline, and keeps a version when the Leaflet has a Leaflet Pro owner
  kind: product
  actor: user
  entities:
  - entity: post
    effect: creates
    facts:
    - Title
    - Description
    - Tags
    - Cover image
    - Published at
    - Content
    - Address
    - Show in Discover
    - Post settings
    - Byline
  - entity: leaflet
    effect: changes
    from: Publication draft
    to: Published
    facts: []
  - entity: leaflet-version
    effect: creates
    facts:
    - Kind
    - Saved at
    - Saved by
    - Snapshot
  - entity: publication
    effect: reads
    facts: []
  - entity: contributor
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publish
- text: With the newsletter on, the Product emails the post to the publication's confirmed email subscribers
  kind: product
  actor: user
  entities:
  - entity: email-subscription
    effect: reads
    facts:
    - Email
    - Unsubscribe link
  - entity: publication
    effect: reads
    facts: []
  - entity: post
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publish
- text: The Product posts the Bluesky post linking to it from the owner's account
  kind: product
  actor: user
  entities:
  - entity: post
    effect: changes
    facts:
    - Bluesky post
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
  target: app/api/inngest/functions/send_post_broadcast.ts
---

# Publish to a publication

## Trigger

An owner or contributor publishes a publication draft.

## Outcome

The post is live in the publication, emailed to its subscribers and shared on Bluesky; a success page links to it and back to the dashboard.

## Edge cases

- A Looseleaf published into a publication moves into it first, gaining a post title block on a canvas.
