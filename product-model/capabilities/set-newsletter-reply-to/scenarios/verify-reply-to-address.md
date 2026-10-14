---
kind: primary
routes:
  web: Web
steps:
- text: The owner enters a reply-to address
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
- text: The Product saves it unverified and emails a code to it
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
- text: The owner enters the code
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-settings
- text: The Product marks the address verified
  kind: product
  actor: user
  entities:
  - entity: publication
    effect: changes
    facts:
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

# Set and verify a reply-to address

## Trigger

An owner wants replies to newsletter emails.

## Outcome

Replies to the publication's emails go to the verified address.

## Edge cases

- The account's own email address is trusted and verified at once, without a code.
- A wrong code leaves the address unverified.
