---
kind: validation
routes:
  web: Web
steps:
- text: The User confirms a merge whose source account already has a Bluesky account
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::merge-accounts
- text: The Product refuses the merge and changes neither account
  kind: condition
  entities:
  - entity: user
    effect: reads
    facts:
    - Bluesky account
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

# An account already linked to Bluesky cannot be merged away

## Trigger

The account to be merged away is not an email-only account, or the target has no Bluesky account.

## Outcome

Both accounts stay as they were.
