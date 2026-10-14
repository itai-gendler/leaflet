---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor opens a person's profile by handle or identifier
  kind: actor
  actor: visitor
  entities:
  - entity: user
    effect: reads
    facts:
    - Profile
    - Bluesky account
  - entity: post
    effect: reads
    facts:
    - Title
    - Published at
  contexts:
    web:
      place: leaflet-web::profile
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/p/[didOrHandle]/page.tsx
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/p/[didOrHandle]/layout.tsx
---

# Open a profile

## Trigger

A reader wants to see more from someone.

## Outcome

The person's posts are shown, with tabs for their comments and subscriptions.
