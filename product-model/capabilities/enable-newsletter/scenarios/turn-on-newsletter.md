---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Enable! on the Newsletter tab
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Leaflet Pro
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
- text: The Product turns newsletter mode on
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

# Turn on the newsletter

## Trigger

An owner wants to email their posts.

## Outcome

Subscribe forms ask for an email address, and posts published from now on are emailed; earlier posts are not.
