---
entities:
- entity: user
  collects:
  - Email
  - Bluesky account
entryPoints:
- leaflet-web: /login/confirm
references:
- kind: code
  role: implementation
  target: components/LoginButton.tsx
- kind: code
  role: implementation
  target: app/login/confirm/page.tsx
---

# Sign in

Where a person logs in with their Bluesky handle or an email address, and enters the code emailed to them.
