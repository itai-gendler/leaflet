---
kind: primary
routes:
  web: Web
steps:
- text: The User picks colors, a background image, fonts or a page width
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Theme
  - entity: page
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product applies the theme to the Leaflet
  kind: product
  actor: user
  entities:
  - entity: leaflet
    effect: changes
    facts:
    - Theme
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
references:
- kind: code
  role: implementation
  target: components/ThemeManager/ThemeSetter.tsx
- kind: code
  role: implementation
  target: components/ThemeManager/themeFacts.ts
---

# Change the theme while signed in

## Trigger

A writer changes how a Leaflet looks.

## Outcome

Everyone sees the Leaflet in its new theme.
