---
kind: primary
routes:
  web: Web
steps:
- text: The User gives a name, description, logo and subdomain, picks Blog or Serial, and creates
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::new-publication
- text: The Product writes the publication to the User's Bluesky account with the default theme and preferences, gives it the leaflet.pub subdomain, and prepares its draft home page
  kind: product
  actor: user
  entities:
  - entity: publication
    effect: creates
    facts:
    - Name
    - Description
    - Logo
    - Address
    - Theme
    - Layout
    - Sharing preferences
    - Pages
    - Newsletter
  - entity: domain
    effect: creates
    facts:
    - Name
    - Assignment
    with: publication
  - entity: leaflet
    effect: reads
    facts: []
  - entity: page
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::new-publication
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/createPub/createPublication.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/createPub/CreatePubForm.tsx
- kind: code
  role: implementation
  target: actions/createPublicationDraftLeaflet.ts
---

# Create a publication

## Trigger

A User with a Bluesky account starts a publication.

## Outcome

The publication exists at its subdomain, owned by the User, and the User lands on a page leading to its dashboard.
