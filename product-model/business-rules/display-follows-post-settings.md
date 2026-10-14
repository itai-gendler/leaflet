---
appliesTo:
- type: capability
  id: read-post
- type: entity
  id: post
  facts:
  - Post settings
references:
- kind: code
  role: implementation
  target: components/PostSettings.tsx
- kind: code
  role: implementation
  target: src/utils/mergePreferences.ts
---

# A post shows comments, mentions and recommends unless its settings or its publication's preferences turn them off

Per-post settings override the publication's sharing preferences; both default to showing everything except first/last buttons.
