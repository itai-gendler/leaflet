---
availability:
- place: leaflet-web::signed-in
domain: leaflet-pro
references:
- kind: code
  role: implementation
  target: actions/createCheckoutSession.ts
- kind: code
  role: implementation
  target: app/api/checkout/success/route.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/upgrade/page.tsx
- kind: code
  role: implementation
  target: stripe/products.ts
---

# Upgrade to Leaflet Pro

Buy Leaflet Pro, monthly or yearly, through the payment provider's checkout.
