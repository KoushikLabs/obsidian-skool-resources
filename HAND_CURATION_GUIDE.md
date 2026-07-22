---
title: Hand-Curation Guide — Japanese Teachings Wiki
type: guide
---

# Hand-Curation Guide

How to review the weekly lint report and write synthesis into
`## Notes` blocks. The `## Notes` section of every concept / entity /
overview / lint page is **hand-editable and preserved across rebuilds.**

## Weekly review checklist

1. Open `wiki/lint.md`. Look at the **Curation leverage ranking** —
   highest `refs × creators` is best ROI for synthesis.
2. Pick the top 1–3 concepts. Open each concept page and write a
   paragraph in `## Notes` describing the cross-creator pattern.
3. Scan **Single-creator items** — niche or coverage gap?
4. Scan **Orphan source pages** — extend the taxonomy in
   `taxonomies/japanese.py` if a real concept appears repeatedly.
5. Scan **Candidate new concepts** — promote any genuine ones to the
   taxonomy.

## Synthesis style
- One paragraph per insight in `## Notes`. Cite pages with `[[wikilink]]`.
- If two creators contradict, record under "### Tensions".
- Keep the rebuild-regenerated content above `## Notes` untouched.
