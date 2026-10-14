---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor picks colors, a background image, fonts or a page width
  kind: actor
  actor: visitor
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
      place: leaflet-web::public::leaflet
- text: The Product applies the theme to the Leaflet
  kind: product
  actor: visitor
  entities:
  - entity: leaflet
    effect: changes
    facts:
    - Theme
  contexts:
    web:
      place: leaflet-web::public::leaflet
references:
- kind: code
  role: implementation
  target: components/ThemeManager/ThemeSetter.tsx
- kind: code
  role: implementation
  target: components/ThemeManager/themeFacts.ts
---

# Change the theme

## Trigger

A writer changes how a Leaflet looks.

## Outcome

Everyone sees the Leaflet in its new theme.

## Edge cases

- A publication draft takes its publication's theme instead of its own.
