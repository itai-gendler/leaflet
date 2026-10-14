---
type: webhook
actors:
- email-delivery-service
references:
- kind: code
  role: implementation
  target: app/api/postmark/webhook/route.ts
---

# Email delivery webhooks

The endpoint Leaflet's email delivery service calls when a newsletter email bounces, is reported as spam, or its recipient unsubscribes from inside their email client.
