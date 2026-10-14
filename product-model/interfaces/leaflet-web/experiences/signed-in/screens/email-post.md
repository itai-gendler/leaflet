---
entities:
- entity: email-post
  shows:
  - Title
  - Description
  - Send mode
  - Send at
  - Problem
  collects:
  - Title
  - Description
  - Send mode
  - Send at
- entity: leaflet
  shows:
  - Title
- entity: publication
  shows:
  - Name
  - Newsletter
  - Pro features
entryPoints:
- leaflet-web: /:leafletId/email
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/[leaflet_id]/email/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(identity)/[leaflet_id]/email/SendEmail.tsx
---

# Send email

Where an email-only draft is given its subject and preview and sent now, later or to each new subscriber.
