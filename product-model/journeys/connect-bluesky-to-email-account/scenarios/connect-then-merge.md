---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User approves the sign-in at a Bluesky account that already has a Leaflet account
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in
  capability: connect-bluesky-account
- text: The Product carries the User to the merge page
  kind: product
  actor: user
  entities:
  - entity: user
    as: email-account
    effect: reads
    facts:
    - Email
  - entity: user
    as: bluesky-account
    effect: reads
    facts:
    - Bluesky account
  - entity: page
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::merge-accounts
  capability: connect-bluesky-account
- text: The User confirms the merge
  kind: actor
  actor: user
  entities:
  - entity: user
    as: email-account
    effect: reads
    facts:
    - Email
  - entity: user
    as: bluesky-account
    effect: reads
    facts:
    - Bluesky account
  contexts:
    web:
      place: leaflet-web::signed-in::merge-accounts
  capability: merge-accounts
- text: The Product merges the email account into the Bluesky account's account and signs in as it
  kind: product
  actor: user
  entities:
  - entity: user
    as: email-account
    effect: removes
  - entity: user
    as: bluesky-account
    effect: changes
    facts:
    - Email
  contexts:
    web:
      place: leaflet-web::signed-in::merge-accounts
  capability: merge-accounts
references:
- kind: code
  role: implementation
  target: actions/mergeIdentity.ts
---

# Connect a Bluesky account that already has an account, then merge

## Trigger

An email-only User connects a Bluesky account that already has its own Leaflet account.

## Outcome

A single account with both sign-ins remains, signed in.
