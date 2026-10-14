---
domain: domains
relations:
- entity: leaflet
  verb: shows
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: actions/domains/index.ts
- kind: code
  role: implementation
  target: app/api/rpc/[command]/domain_routes.ts
---

# Domain

A custom domain a person registers and points at one of their Leaflets or at one of their publications.

## Information kept

- **Name** — the domain, without a leading www
- **Status** — pending until its DNS records verify, then ready
- **Assignment** — what it points at: nothing, Leaflets at chosen routes, or a publication
- **Route** — for a Leaflet, the path on the domain it answers at
