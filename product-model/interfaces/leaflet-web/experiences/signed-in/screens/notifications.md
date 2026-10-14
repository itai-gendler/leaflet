---
entities:
- entity: notification
  shows:
  - Kind
  - Subject
  - Created at
entryPoints:
- leaflet-web: /notifications
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/notifications/page.tsx
---

# Notifications

The signed-in person's notifications.
