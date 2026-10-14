---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses New Draft in a publication's dashboard
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
- text: The Product creates a Leaflet as a draft of the publication and opens it; a contributor is credited on it
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
  - entity: publication
    effect: reads
    facts: []
  - entity: contributor
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
references:
- kind: code
  role: implementation
  target: actions/createPublicationDraft.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/NewDraftButton.tsx
---

# Start a new draft

## Trigger

An owner or contributor starts writing a post.

## Outcome

A new draft is open in the editor and listed among the publication's drafts.

## Edge cases

- An email-only draft goes out through Send Email rather than Publish.
- A canvas draft starts with a post title block for its metadata.
