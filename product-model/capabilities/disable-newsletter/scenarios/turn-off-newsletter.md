---
kind: primary
routes:
  web: Web
steps:
- text: The owner confirms disabling the newsletter
  kind: actor
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Newsletter
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
- text: The Product turns newsletter mode off
  kind: product
  actor: user
  entities:
  - entity: publication
    effect: changes
    facts:
    - Newsletter
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

# Turn off the newsletter

## Trigger

An owner stops emailing.

## Outcome

No more emails go out and readers subscribe with Bluesky again; email subscribers are kept for re-enabling.
