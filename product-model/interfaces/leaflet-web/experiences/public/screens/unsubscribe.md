---
entities:
- entity: email-subscription
  shows:
  - Email
entryPoints:
- leaflet-web: /emails/unsubscribe
references:
- kind: code
  role: implementation
  target: app/emails/unsubscribe/route.ts
---

# Unsubscribed

The page an email's unsubscribe link opens, confirming the address is unsubscribed.
