---
kind: primary
routes:
  web: Web
steps:
- text: The owner picks colors, a background, fonts and a width and saves
  kind: actor
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Theme
  contexts:
    web:
      place: leaflet-web::signed-in::publication-theme
- text: The Product saves the theme to the publication
  kind: product
  actor: user
  entities:
  - entity: publication
    effect: changes
    facts:
    - Theme
  contexts:
    web:
      place: leaflet-web::signed-in::publication-theme
references:
- kind: code
  role: implementation
  target: actions/publications/updatePublication.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/theme-settings/ThemeSettingsContent.tsx
---

# Save the theme

## Trigger

An owner restyles their publication.

## Outcome

The publication and all its posts show the new theme.
