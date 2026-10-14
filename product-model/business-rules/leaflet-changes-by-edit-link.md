---
appliesTo:
- type: entity
  id: leaflet
  effect: changes
  facts:
  - Title
  - Description
  - Theme
  - View link
  - Post settings
permits:
- actors:
  - visitor
  - user
references:
- kind: code
  role: implementation
  target: components/ThemeManager/ThemeSetter.tsx
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/actions/ShareOptions/getShareLink.ts
---

# Anyone with a Leaflet's edit link changes its title, theme, view link and post settings

These belong to the Leaflet, not to a person: whoever holds the edit link, signed in or not, changes them.
