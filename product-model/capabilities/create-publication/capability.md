---
availability:
- place: leaflet-web::signed-in
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

Create a blog or newsletter in one's Bluesky account, with a name, optional description and logo, and a leaflet.pub subdomain as its address.
