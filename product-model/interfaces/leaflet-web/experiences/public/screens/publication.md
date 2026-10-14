---
entities:
- entity: publication
  shows:
  - Name
  - Description
  - Logo
  - Theme
  - Pages
  - Recommended publications
  - Newsletter
- entity: post
  shows:
  - Title
  - Description
  - Published at
- entity: email-subscription
  collects:
  - Email
entryPoints:
- leaflet-web: /lish/:did/:publication
- leaflet-web: /subscribe/:did/:rkey
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/DefaultPublicationHomepage.tsx
---

# Publication

A publication's home page, pages and archive, with its subscribe form.
