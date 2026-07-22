---
title: "Easiest Way to Migrate n8n Workflows Between Accounts (cloud to self-hosted)"
date: 2026-01-14
creator: nate-herk
youtube: https://youtu.be/t1PTmpas0bg
source_url: https://drive.google.com/drive/folders/1iRWNtD8XogUl3XTuFct3ciRMT6w9EWgJ
type: source
concepts:
  - workflow-automation
  - self-hosting
entities:
  - n8n
  - google
---

# Easiest Way to Migrate n8n Workflows Between Accounts (cloud to self-hosted)

> Step-by-step n8n workflow migration between cloud and self-hosted

## Links
- Watch: https://youtu.be/t1PTmpas0bg
- Original source bundle: https://drive.google.com/drive/folders/1iRWNtD8XogUl3XTuFct3ciRMT6w9EWgJ
- Raw artefacts: `../../raw/easiest-way-to-migrate-n8n-workflows-between-accounts-cloud/` (1 files)
- Creator: [[nate-herk-profile]]

## Cross-references
**Concepts:** [[workflow-automation]], [[self-hosting]]
**Entities:** [[n8n]], [[google]]

## Files
- [`Migrate Workflows (1).json`](../../raw/easiest-way-to-migrate-n8n-workflows-between-accounts-cloud/Migrate Workflows (1).json) — 12.0 KB

---

## Migrate Workflows (1).json
_n8n workflow — [open JSON](../../raw/easiest-way-to-migrate-n8n-workflows-between-accounts-cloud/Migrate Workflows (1).json)_

**Workflow:** `Migrate Workflows`

**Total nodes:** 13

**Triggers:** When clicking ‘Execute workflow’

**Node-type counts:** `stickyNote`×4, `n8n`×3, `googleSheets`×3, `splitInBatches`×2, `manualTrigger`×1


**Nodes:**
- **When clicking ‘Execute workflow’** — `manualTrigger`
- **Get many workflows** — `n8n`
- **Loop Over Items** — `splitInBatches`
- **Create a workflow** — `n8n`
- **Append row in sheet** — `googleSheets`
- **Get a workflow** — `n8n`
- **Update row in sheet** — `googleSheets`
- **Sticky Note** — `stickyNote`
- **Sticky Note1** — `stickyNote`
- **Sticky Note2** — `stickyNote`
- **Sticky Note3** — `stickyNote`
- **Loop** — `splitInBatches`
- **Get Workflow IDs** — `googleSheets`
