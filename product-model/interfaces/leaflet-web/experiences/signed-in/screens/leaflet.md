---
entities:
- entity: leaflet
  shows:
  - Title
  - Description
  - Pages
  - Theme
  - Edit link
  - View link
  - Post settings
  collects:
  - Post settings
- entity: page
  shows:
  - Kind
  - Blocks
- entity: block
  shows:
  - Type
  - Content
  - Position
  - Poll options
  collects:
  - Content
  - Poll options
- entity: poll-vote
  collects:
  - Options
- entity: post
  shows:
  - Address
- entity: leaflet-comment
  shows:
  - Text
  - Author
  - Quoted passage
  - Replies
  - Written at
  collects:
  - Text
  - Replies
- entity: domain
  shows:
  - Name
  - Route
  collects:
  - Route
- entity: publication
  shows:
  - Name
entryPoints:
- leaflet-web: /:leafletId
references:
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/Leaflet.tsx
- kind: code
  role: implementation
  target: components/EditorComments/AnnotationSideColumn.tsx
---

# Leaflet

A Leaflet open while signed in: everything the edit link allows, plus comments, Save to Home, publishing, post settings, custom domains and the version history entry point.
