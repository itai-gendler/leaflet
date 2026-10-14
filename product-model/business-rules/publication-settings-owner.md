---
appliesTo:
- type: entity
  id: publication
  effect: changes
  facts:
  - Name
  - Description
  - Logo
  - Theme
  - Layout
  - Sharing preferences
  - Recommended publications
  - Pages
  - Reply-to email
  - Reply-to verified
permits:
- related:
  - verb: owns
    entity: user
references:
- kind: code
  role: implementation
  target: actions/publications/updatePublication.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/SettingsContent.tsx
- kind: code
  role: implementation
  target: actions/publications/newsletterSettings.tsx
- kind: code
  role: implementation
  target: src/utils/publishPublicationPages.ts
---

# Only a publication's owner changes its settings

Name, description, logo, theme, layout, sharing preferences, recommendations, published pages and the reply-to address are the owner's to change. Contributors see only their contributor view of the settings.
