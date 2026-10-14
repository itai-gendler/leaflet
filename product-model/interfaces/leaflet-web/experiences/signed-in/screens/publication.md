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
- entity: subscription
  shows:
  - Subscribed at
- entity: email-subscription
  shows:
  - Email
  collects:
  - Email
- entity: user
  shows:
  - Email
entryPoints:
- leaflet-web: /lish/:did/:publication
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/DefaultPublicationHomepage.tsx
- kind: code
  role: implementation
  target: components/Subscribe/ManageSubscribe.tsx
---

# Publication

A publication as a signed-in reader sees it, where they subscribe, manage their subscription and recommend it from their own publications.
