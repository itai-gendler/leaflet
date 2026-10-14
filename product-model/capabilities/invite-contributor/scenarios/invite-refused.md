---
kind: validation
routes:
  web: Web
steps:
- text: The owner enters a handle that does not resolve, their own handle, or someone already invited
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
- text: The Product refuses and says why
  kind: condition
  entities: []
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

# An invitation is refused

## Trigger

The handle cannot be invited.

## Outcome

No invitation is recorded.
