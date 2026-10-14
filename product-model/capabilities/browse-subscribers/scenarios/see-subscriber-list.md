---
kind: primary
routes:
  web: Web
steps:
- text: The User opens the Subscribers tab
  kind: actor
  actor: user
  entities:
  - entity: subscription
    effect: reads
    facts:
    - Subscribed at
  - entity: email-subscription
    effect: reads
    facts:
    - Email
    - Confirmed at
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/PublicationSubscribers.tsx
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/mergeSubscribers.ts
---

# See the subscribers

## Trigger

An owner or contributor checks who follows the publication.

## Outcome

Subscribers show as subscribed, unconfirmed or unsubscribed, merged by person.
