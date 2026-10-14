---
kind: primary
routes:
  web: Web
steps:
- text: The User opens notifications
  kind: actor
  actor: user
  entities:
  - entity: notification
    effect: reads
    facts:
    - Kind
    - Subject
    - Created at
  contexts:
    web:
      place: leaflet-web::signed-in::notifications
- text: The Product marks all of the User's notifications read
  kind: product
  actor: user
  entities:
  - entity: notification
    effect: changes
    from: Unread
    to: Read
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::notifications
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/notifications/NotificationList.tsx
- kind: code
  role: implementation
  target: actions/getNotifications.ts
---

# Read notifications

## Trigger

A User sees they have new notifications.

## Outcome

The notifications are listed, grouped where they repeat, and no longer counted as new.
