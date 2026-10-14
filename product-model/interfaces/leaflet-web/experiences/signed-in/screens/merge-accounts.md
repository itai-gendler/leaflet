---
entities:
- entity: user
  shows:
  - Email
  - Bluesky account
entryPoints:
- leaflet-web: /merge-accounts
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/merge-accounts/page.tsx
---

# Merge accounts

Where a person decides whether to merge their email account into the account of the Bluesky account they connected.
