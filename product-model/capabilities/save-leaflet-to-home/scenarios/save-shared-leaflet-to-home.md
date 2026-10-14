---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Save to Home on a Leaflet
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product adds the Leaflet to the User's Home
  kind: product
  actor: user
  entities:
  - entity: home-leaflet
    effect: creates
    to: On Home
    facts:
    - Added at
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
references:
- kind: code
  role: implementation
  target: actions/addLeafletToHome.ts
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/actions/HomeButton.tsx
---

# Save a shared Leaflet to Home

## Trigger

A User opened a Leaflet by its link and wants to find it again.

## Outcome

The Leaflet is listed on the User's Home.
