---
domain: subscriptions
references:
- kind: code
  role: implementation
  target: actions/publications/subscribeEmail.tsx
- kind: code
  role: implementation
  target: src/subscriptions/email.ts
- kind: code
  role: implementation
  target: drizzle/schema.ts
---

# Email subscription

A reader's subscription to a publication's newsletter at an email address.

## Information kept

- **Email** — the address emails go to
- **Confirmed at** — when the address was confirmed
- **Unsubscribed at** — when it stopped
- **Unsubscribe link** — the link in each email that unsubscribes this address

## States

### Pending

Waiting for the reader to enter the code sent to the address.

### Confirmed

Receives the publication's emails.

### Unsubscribed

Receives nothing; subscribing again reuses it.
