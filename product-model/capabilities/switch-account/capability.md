---
availability:
- place: leaflet-web::signed-in
references:
- kind: code
  role: implementation
  target: app/api/auth/switch-account/route.ts
- kind: code
  role: implementation
  target: actions/savedAccounts.ts
- kind: code
  role: implementation
  target: components/ActionBar/AccountSwitcher.tsx
---

# Switch account

Move between the accounts this browser has signed in to, or sign in to another account alongside the current one.
