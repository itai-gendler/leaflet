---
availability:
- place: leaflet-web::signed-in
domain: publication-dashboard
references:
- kind: code
  role: implementation
  target: app/api/rpc/[command]/get_publication_analytics.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/analytics/PublicationAnalytics.tsx
---

# View publication analytics

See a publication's traffic, top referrers and pages, subscriber growth and the Bluesky posts linking to it. A Leaflet Pro feature for the owner.
