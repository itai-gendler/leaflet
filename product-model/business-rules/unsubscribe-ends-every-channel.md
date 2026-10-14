---
appliesTo:
- type: capability
  id: unsubscribe-from-publication
- type: capability
  id: unsubscribe-by-email-link
- type: entity
  id: email-subscription
  facts:
  - Unsubscribed at
references:
- kind: code
  role: implementation
  target: src/subscriptions/unsubscribe.ts
---

# Unsubscribing from a publication ends both the Bluesky and the email subscription

From the subscription panel or an email's unsubscribe link, unsubscribing leaves no channel behind.
