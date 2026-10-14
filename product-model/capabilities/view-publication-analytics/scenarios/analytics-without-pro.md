---
kind: validation
routes:
  web: Web
steps:
- text: An owner without Leaflet Pro opens the Analytics tab
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Leaflet Pro
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
- text: The Product shows no figures and offers Leaflet Pro
  kind: condition
  entities:
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
references:
- kind: code
  role: implementation
  target: app/api/rpc/[command]/get_publication_analytics.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/analytics/PublicationAnalytics.tsx
---

# Analytics without Leaflet Pro

## Trigger

The owner has no Leaflet Pro.

## Outcome

No analytics are shown.
