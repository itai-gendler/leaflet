---
kind: primary
routes:
  web: Web
steps:
- text: The owner opens the Analytics tab and picks a date range, a post or a referrer
  kind: actor
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Analytics
  - entity: post
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

# See the publication's analytics

## Trigger

An owner wants to know how the publication is read.

## Outcome

Charts show visits, referrers, pages and subscribers for the range.
