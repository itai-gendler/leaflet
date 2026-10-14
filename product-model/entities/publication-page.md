---
domain: publication-settings
references:
- kind: code
  role: implementation
  target: src/utils/publishPublicationPages.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/edit/PublicationPagesEditNav.tsx
---

# Publication page

A page in a publication's navigation: a page written in the publication's draft, or a link to somewhere else.

## Information kept

- **Title** — the name shown in the navigation
- **Kind** — a page of the publication, or an external link
- **Path** — the page's path under the publication's address, or the link's URL
- **Order** — its place in the navigation
