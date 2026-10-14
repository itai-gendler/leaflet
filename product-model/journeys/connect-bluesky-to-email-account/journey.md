---
actors:
- user
references:
- kind: code
  role: implementation
  target: app/api/oauth/[route]/route.ts
- kind: code
  role: implementation
  target: actions/mergeIdentity.ts
---

# Connect Bluesky to an email account

## Goal

A person who signs in by email ends with one account that also has their Bluesky account.

## Success criterion

One account holds both the email and the Bluesky account.
