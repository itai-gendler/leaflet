---
entities:
- entity: leaflet
  shows:
  - Title
  - Description
  - Post settings
  collects:
  - Title
  - Description
- entity: post
  collects:
  - Tags
  - Cover image
  - Published at
  - Show in Discover
- entity: tag
  collects:
  - Name
- entity: scheduled-post
  shows:
  - Publish at
  - Problem
  collects:
  - Publish at
  - Sharing
- entity: publication
  shows:
  - Name
  - Newsletter
  - Pro features
entryPoints:
- leaflet-web: /:leafletId/publish
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/[leaflet_id]/publish/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(identity)/[leaflet_id]/publish/PublishPost.tsx
---

# Publish

Where a draft is published: post details, where it goes, its Bluesky post, email, Discover, quiet posting, date and schedule, and a preview email.
