---
appliesTo:
- type: capability
  id: view-publication-analytics
- type: capability
  id: enable-newsletter
- type: capability
  id: schedule-post
- type: capability
  id: invite-contributor
- type: entity
  id: publication
  facts:
  - Pro features
references:
- kind: code
  role: implementation
  target: src/entitlements.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/upgrade/page.tsx
---

# Leaflet Pro unlocks analytics, email newsletters, post scheduling, group publications and version history

Contributors use their publication owner's Leaflet Pro; a lapsed plan pauses scheduled and email posts rather than dropping them.
