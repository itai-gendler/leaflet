---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses options in a poll and votes
  kind: actor
  actor: user
  entities:
  - entity: block
    effect: reads
    facts:
    - Poll options
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product records the vote for this voter and shows the results
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
      place: leaflet-web::signed-in::leaflet
references:
- kind: code
  role: implementation
  target: actions/pollActions.ts
---

# Vote in a poll while signed in

## Trigger

A reader or writer answers a poll in a Leaflet.

## Outcome

The vote counts once for this voter and the results show.
