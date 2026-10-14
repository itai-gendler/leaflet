---
entities:
- entity: publication
  shows:
  - Name
  - Analytics
- entity: user
  shows:
  - Leaflet Pro
- entity: leaflet
  shows:
  - Title
  - Description
- entity: post
  shows:
  - Title
  - Published at
  - Recommends
- entity: scheduled-post
  shows:
  - Publish at
  - Problem
- entity: email-post
  shows:
  - Title
  - Send mode
  - Send at
  - Recipients
  - Sent at
  - Problem
- entity: subscription
  shows:
  - Subscribed at
- entity: email-subscription
  shows:
  - Email
  - Confirmed at
entryPoints:
- leaflet-web: /lish/:did/:publication/dashboard
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/layout.tsx
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/page.tsx
---

# Publication dashboard

A publication's drafts, scheduled and published posts, email posts, subscribers and analytics.
