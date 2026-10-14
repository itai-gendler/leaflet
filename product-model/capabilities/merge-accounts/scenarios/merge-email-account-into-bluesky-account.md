---
kind: primary
routes:
  web: Web
steps:
- text: The User confirms merging their email account into the Bluesky account's account
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
- text: The Product moves the email account's Leaflets, subscriptions and Leaflet Pro into the Bluesky account's account, removes the email account and signs in as the merged account
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
  - entity: subscription
    effect: reads
    facts: []
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::merge-accounts
references:
- kind: code
  role: implementation
  target: actions/mergeIdentity.ts
- kind: code
  role: implementation
  target: src/mergeIdentity.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/merge-accounts/page.tsx
---

# Merge an email account into a Bluesky account

## Trigger

A User who connected a Bluesky account belonging to another Leaflet account confirms the merge.

## Outcome

One account remains, signed in, with the email and the Bluesky account and everything the two accounts held.

## Edge cases

- Where both accounts hold the same thing, the Bluesky account's own copy is kept.
