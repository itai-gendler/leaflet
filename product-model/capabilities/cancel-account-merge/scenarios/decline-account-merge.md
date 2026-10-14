---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses not to merge the accounts
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Email
    - Bluesky account
  contexts:
    web:
      place: leaflet-web::signed-in::merge-accounts
- text: The Product drops the pending merge and stays signed in as the email account
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::merge-accounts
references:
- kind: code
  role: implementation
  target: actions/mergeIdentity.ts
---

# Decline merging two accounts

## Trigger

A User on the merge page declines.

## Outcome

Both accounts remain separate and the email account stays signed in.
