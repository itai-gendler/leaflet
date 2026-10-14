---
entities:
- entity: pro-subscription
  collects:
  - Plan
- entity: user
  shows:
  - Leaflet Pro
entryPoints:
- leaflet-web: /upgrade
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/upgrade/page.tsx
---

# Get Leaflet Pro

Where a person chooses a Leaflet Pro plan and goes to checkout.
