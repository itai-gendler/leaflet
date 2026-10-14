---
kind: validation
routes:
  web: Web
steps:
- text: The User gives a subdomain shorter than 3 or longer than 63 characters, or with characters other than lowercase letters, digits and hyphens
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::new-publication
- text: The Product refuses and creates nothing
  kind: condition
  entities: []
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

# An invalid subdomain is refused

## Trigger

The chosen address is not a valid subdomain.

## Outcome

No publication is created.

## Edge cases

- A User signed in by email only is asked to connect a Bluesky account first.
