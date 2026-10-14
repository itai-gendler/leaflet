---
kind: primary
routes:
  web: Web
steps:
- text: The owner removes the reply-to address
  kind: actor
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Reply-to email
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
- text: The Product clears it
  kind: product
  actor: user
  entities:
  - entity: publication
    effect: changes
    facts:
    - Reply-to email
    - Reply-to verified
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
references:
- kind: code
  role: implementation
  target: actions/publications/newsletterSettings.tsx
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/NewsletterSettings.tsx
---

# Clear the reply-to address

## Trigger

An owner no longer wants replies at that address.

## Outcome

Newsletter emails go out without a reply-to address.
