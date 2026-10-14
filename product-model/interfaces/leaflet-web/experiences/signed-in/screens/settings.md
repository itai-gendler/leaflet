---
entities:
- entity: user
  shows:
  - Email
  - Leaflet Pro
  collects:
  - Email
- entity: domain
  shows:
  - Name
  - Status
  - Assignment
  - Route
  collects:
  - Name
- entity: pro-subscription
  shows:
  - Plan
  - Period end
entryPoints:
- leaflet-web: /settings
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/settings/SettingsPageContent.tsx
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/settings/domains/DomainTab.tsx
---

# Settings

The account's settings: its email and domains, billing, and Leaflet Pro.
