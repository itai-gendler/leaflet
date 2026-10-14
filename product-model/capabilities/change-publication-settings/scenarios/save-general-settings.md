---
kind: primary
routes:
  web: Web
steps:
- text: The owner changes settings on the General tab and saves
  kind: actor
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Name
    - Description
    - Logo
    - Layout
    - Sharing preferences
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
- text: The Product rewrites the publication's record in the owner's Bluesky account
  kind: product
  actor: user
  entities:
  - entity: publication
    effect: changes
    facts:
    - Name
    - Description
    - Logo
    - Layout
    - Sharing preferences
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
references:
- kind: code
  role: implementation
  target: actions/publications/updatePublication.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/SettingsContent.tsx
---

# Save the publication's settings

## Trigger

A publication's owner adjusts how it presents itself.

## Outcome

Readers see the publication with its new settings; the owner sees Settings saved.

## Edge cases

- An expired Bluesky sign-in is reported with a way to sign in again, and nothing is saved.
