---
entities:
- entity: publication
  shows:
  - Name
  - Description
  - Logo
  - Layout
  - Sharing preferences
  - Recommended publications
  - Newsletter
  - Reply-to email
  - Reply-to verified
  collects:
  - Name
  - Description
  - Logo
  - Layout
  - Sharing preferences
  - Recommended publications
  - Reply-to email
- entity: contributor
  shows:
  - Accepted
  - Invited at
- entity: domain
  shows:
  - Name
  - Status
- entity: user
  shows:
  - Leaflet Pro
entryPoints:
- leaflet-web: /lish/:did/:publication/dashboard/settings
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/SettingsContent.tsx
---

# Publication settings

A publication's settings: General (name, logo, recommendations, layout, sharing, domains, deletion), Contributors and Newsletter. Contributors see only their own contributor view.
