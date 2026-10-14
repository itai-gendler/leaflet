---
domain: subscriptions
references:
- kind: code
  role: implementation
  target: src/subscriptions/atproto.ts
- kind: code
  role: implementation
  target: actions/publications/subscribeToPublication.ts
---

# Subscription

A reader's subscription to a publication through their Bluesky account, kept as a record in that account.

## Information kept

- **Subscribed at** — when they subscribed
