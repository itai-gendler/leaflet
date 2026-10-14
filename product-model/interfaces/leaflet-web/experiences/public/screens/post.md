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
- entity: publication
  shows:
  - Name
  - Logo
  - Theme
  - Layout
  - Newsletter
- entity: email-subscription
  collects:
  - Email
entryPoints:
- leaflet-web: /lish/:did/:publication/:rkey
- leaflet-web: /p/:handle/:rkey
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/Interactions/Interactions.tsx
---

# Post

A published post as anyone reads it, with its discussion, quotes and the publication's subscribe form.
