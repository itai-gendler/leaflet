---
kind: validation
routes:
  web: Web
steps:
- text: A User who was not invited opens the invitation and accepts
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::contributor-invitation
- text: 'The Product refuses: they were not invited'
  kind: condition
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::contributor-invitation
references:
- kind: code
  role: implementation
  target: actions/publications/contributors.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/ContributorSettings.tsx
---

# Accepting without an invitation is refused

## Trigger

Someone without an invitation tries to join.

## Outcome

Nothing changes.
