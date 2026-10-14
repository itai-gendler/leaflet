---
availability:
- place: leaflet-web::signed-in
domain: domains
references:
- kind: code
  role: implementation
  target: app/api/rpc/[command]/domain_routes.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/settings/domains/useDomainStatus.ts
---

# Check a domain's status

Check whether a domain's DNS is set up, asking the host to verify it again.
