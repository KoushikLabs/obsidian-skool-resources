---
title: "I Built an AI System That Automates My Proposals (n8n + Gamma)"
date: 2026-01-19
creator: nate-herk
youtube: https://youtu.be/KGXFkUlBHxw
source_url: https://drive.google.com/drive/folders/1JspZDqbygDUrTaO9mJYqHUbbQPodiNam
type: source
concepts:
  - workflow-automation
  - proposal-generation
entities:
  - n8n
  - google
  - gamma
  - openrouter
---

# I Built an AI System That Automates My Proposals (n8n + Gamma)

> AI system that auto-generates client proposals using n8n and Gamma

## Links
- Watch: https://youtu.be/KGXFkUlBHxw
- Original source bundle: https://drive.google.com/drive/folders/1JspZDqbygDUrTaO9mJYqHUbbQPodiNam
- Raw artefacts: `../../raw/i-built-an-ai-system-that-automates-my-proposals-n8n-gamma/` (1 files)
- Creator: [[nate-herk-profile]]

## Cross-references
**Concepts:** [[workflow-automation]], [[proposal-generation]]
**Entities:** [[n8n]], [[google]], [[gamma]], [[openrouter]]

## Files
- [`Gamma Proposal Generation.json`](../../raw/i-built-an-ai-system-that-automates-my-proposals-n8n-gamma/Gamma Proposal Generation.json) — 36.2 KB

---

## Gamma Proposal Generation.json
_n8n workflow — [open JSON](../../raw/i-built-an-ai-system-that-automates-my-proposals-n8n-gamma/Gamma Proposal Generation.json)_

**Workflow:** `Gamma Proposal Generation`

**Total nodes:** 26

**Triggers:** On form submission, Google Sheets Trigger

**Node-type counts:** `fireflies`×3, `code`×3, `stickyNote`×3, `googleSheets`×3, `slack`×2, `if`×2, `set`×2, `webhook`×1, `lmChatOpenRouter`×1, `agent`×1, `httpRequest`×1, `formTrigger`×1, `googleSheetsTrigger`×1, `limit`×1, `wait`×1


**Nodes:**
- **Webhook** — `webhook`
- **Get Meeting Info** — `fireflies`
- **Clean Up** — `code`
- **Proposal Generation?** — `slack`
- **If** — `if`
- **OpenRouter** — `lmChatOpenRouter`
- **Proposal Generator Agent** — `agent`
- **Gamma Deck** — `httpRequest`
- **Notification** — `slack`
- **On form submission** — `formTrigger`
- **Get Meeting Info1** — `fireflies`
- **Clean Up1** — `code`
- **Set Transcript** — `set`
- **Get Info** — `fireflies`
- **Google Sheets Trigger** — `googleSheetsTrigger`
- **Limit** — `limit`
- **Sticky Note** — `stickyNote`
- **Sticky Note1** — `stickyNote`
- **Wait** — `wait`
- **If1** — `if`
- **Generation Declined** — `googleSheets`
- **Standardize** — `set`
- **Generated** — `googleSheets`
- **Log Meeting** — `googleSheets`
- **Attendees** — `code`
- **Sticky Note2** — `stickyNote`
