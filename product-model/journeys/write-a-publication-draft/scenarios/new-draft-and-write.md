---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User chooses New Draft in the publication's dashboard
  kind: actor
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
  capability: create-publication-draft
- text: The Product creates the draft and opens it in the editor
  kind: product
  actor: user
  entities:
  - entity: leaflet
    effect: creates
    to: Publication draft
    facts:
    - Pages
    - Edit link
  - entity: page
    effect: creates
    facts:
    - Kind
    - Blocks
    with: leaflet
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
  capability: create-publication-draft
- text: The User writes in the draft
  kind: actor
  actor: user
  entities:
  - entity: block
    effect: changes
    facts:
    - Content
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
  capability: edit-block
references:
- kind: code
  role: implementation
  target: actions/createPublicationDraft.ts
---

# Start a draft from the dashboard and write

## Trigger

A writer starts a post from the dashboard.

## Outcome

The draft is listed in the dashboard with what was written.
