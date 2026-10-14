---
appliesTo:
- type: capability
  id: report-delivery-problem
- type: entity
  id: email-subscription
  facts:
  - Unsubscribed at
references:
- kind: code
  role: implementation
  target: src/subscriptions/email.ts
- kind: code
  role: implementation
  target: actions/publications/subscribeEmail.tsx
- kind: code
  role: implementation
  target: app/api/postmark/webhook/route.ts
---

# Addresses that hard-bounce or report spam are unsubscribed

A hard bounce or spam complaint unsubscribes that subscription; a one-click unsubscribe from the email client unsubscribes the address from every publication; soft bounces change nothing.
