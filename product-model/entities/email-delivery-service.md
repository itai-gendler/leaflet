---
kind: system
acts: external
references:
- kind: code
  role: implementation
  target: app/api/postmark/webhook/route.ts
---

# Email delivery service

The service that delivers Leaflet's newsletter emails and reports back bounces, spam complaints and one-click unsubscribes.
