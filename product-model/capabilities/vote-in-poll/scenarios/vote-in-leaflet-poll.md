---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor chooses options in a poll and votes
  kind: actor
  actor: visitor
  entities:
  - entity: block
    effect: reads
    facts:
    - Poll options
  contexts:
    web:
      place: leaflet-web::public::leaflet
- text: The Product records the vote for this voter and shows the results
  kind: product
  actor: visitor
  entities:
  - entity: poll-vote
    effect: creates
    facts:
    - Options
    - Voter
  contexts:
    web:
      place: leaflet-web::public::leaflet
references:
- kind: code
  role: implementation
  target: actions/pollActions.ts
---

# Vote in a poll

## Trigger

A reader or writer answers a poll in a Leaflet.

## Outcome

The vote counts once for this voter and the results show.

## Edge cases

- Voting again from the same browser or account replaces the earlier vote.
