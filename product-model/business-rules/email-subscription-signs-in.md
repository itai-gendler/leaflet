---
appliesTo:
- type: capability-scenario
  id: subscribe-by-email-signed-out
- type: entity
  id: user
  facts:
  - Email
references:
- kind: code
  role: implementation
  target: app/api/auth/email-login/route.ts
- kind: code
  role: implementation
  target: src/subscriptions/email.ts
---

# Subscribing by email signs the reader in to the account for that address

Confirming the emailed code both confirms the subscription and signs the reader in, creating a Leaflet account for a new address.
