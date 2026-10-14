---
kind: person
acts: external
relations:
- entity: publication
  verb: owns
  cardinality: one-to-many
- entity: domain
  verb: owns
  cardinality: one-to-many
- entity: home-leaflet
  verb: keeps
  cardinality: one-to-many
- entity: contributor
  verb: holds
  cardinality: one-to-many
- entity: pro-subscription
  verb: pays for
  cardinality: one-to-one
- entity: post
  verb: publishes
  cardinality: one-to-many
- entity: subscription
  verb: subscribes with
  cardinality: one-to-many
- entity: email-subscription
  verb: receives emails through
  cardinality: one-to-many
- entity: recommendation
  verb: gives
  cardinality: one-to-many
- entity: post-comment
  verb: writes
  cardinality: one-to-many
- entity: notification
  verb: receives
  cardinality: one-to-many
- entity: leaflet-comment
  verb: authors
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/auth.ts
- kind: code
  role: implementation
  target: actions/getIdentityData.ts
- kind: code
  role: implementation
  target: src/identityPayload.ts
---

# User

A person signed in to Leaflet with a Bluesky account, an email address or both. A user owns the publications they create and the domains they register, keeps Leaflets on Home, contributes to publications they are invited to, subscribes, recommends and comments.

## Information kept

- **Email** — the email address the account signs in with by code and receives subscription emails at
- **Bluesky account** — the Bluesky (AT Protocol) account connected to the Leaflet account: its handle and identifier
- **Profile** — the display name, avatar and description shown from the Bluesky profile
- **Leaflet Pro** — whether the account currently holds Leaflet Pro, through its subscription or a grant from the Leaflet team
