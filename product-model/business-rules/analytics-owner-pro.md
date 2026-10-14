---
appliesTo:
- type: entity
  id: publication
  effect: reads
  facts:
  - Analytics
permits:
- related:
  - verb: owns
    entity: user
  when:
  - entity: user
    fact: Leaflet Pro
    is: true
references:
- kind: code
  role: implementation
  target: app/api/rpc/[command]/get_publication_analytics.ts
- kind: code
  role: implementation
  target: app/api/rpc/[command]/get_publication_subscribers_timeseries.ts
---

# Only a publication's owner with Leaflet Pro reads its analytics

Traffic, referrers, pages, subscriber growth and linking Bluesky posts are shown to the owner while they hold Leaflet Pro.
