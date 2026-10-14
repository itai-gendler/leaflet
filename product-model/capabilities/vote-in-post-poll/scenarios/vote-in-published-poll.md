---
kind: primary
routes:
  web: Web
steps:
- text: The User votes in a post's poll
  kind: actor
  actor: user
  entities:
  - entity: post
    effect: reads
    facts:
    - Content
  contexts:
    web:
      place: leaflet-web::signed-in::post
- text: The Product records the vote in the User's Bluesky account
  kind: product
  actor: user
  entities:
  - entity: poll-vote
    effect: creates
    facts:
    - Options
    - Voter
  contexts:
    web:
      place: leaflet-web::signed-in::post
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/voteOnPublishedPoll.ts
---

# Vote in a published poll

## Trigger

A signed-in reader answers a poll in a post.

## Outcome

The vote counts and results show.
