---
availability:
- place: email-delivery-webhooks
domain: subscriptions
references:
- kind: code
  role: implementation
  target: app/api/postmark/webhook/route.ts
---

# Report an email delivery problem

The email delivery service reports a bounce, a spam complaint or a one-click unsubscribe, and the address stops receiving emails.
