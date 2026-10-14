---
kind: primary
routes:
  web: Web
steps:
- text: The owner enters a Bluesky handle and invites
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Leaflet Pro
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
- text: The Product records the invitation
  kind: product
  actor: user
  entities:
  - entity: contributor
    effect: creates
    facts:
    - Accepted
    - Invited at
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
references:
- kind: code
  role: implementation
  target: actions/publications/contributors.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/ContributorSettings.tsx
---

# Invite a contributor

## Trigger

An owner wants someone else to write for the publication.

## Outcome

The invitee is listed as invited until they accept.
