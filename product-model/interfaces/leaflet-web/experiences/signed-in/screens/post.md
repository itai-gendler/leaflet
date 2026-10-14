---
entities:
- entity: post
  shows:
  - Title
  - Description
  - Tags
  - Cover image
  - Published at
  - Content
  - Byline
  - Recommends
  - Post settings
- entity: post-comment
  shows:
  - Text
  - Quoted passage
  - In reply to
  - Posted at
  collects:
  - Text
- entity: publication
  shows:
  - Name
  - Logo
  - Theme
  - Layout
  - Newsletter
- entity: recommendation
  shows:
  - Recommended at
- entity: subscription
  shows:
  - Subscribed at
entryPoints:
- leaflet-web: /lish/:did/:publication/:rkey
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/Interactions/Interactions.tsx
---

# Post

A published post as a signed-in reader sees it: reading, recommending, commenting, voting and managing their subscription.
