---
title: Operating Manual — Japanese Teachings Wiki
type: manual
---

# Operating Manual

Routine operations for the **japanese** pipeline. Treat this as the
canonical runbook — update when commands or schedules change.

## Daily
- 06:xx — `youtube_watcher.py --domain japanese` polls RSS feeds, queues new long-form videos.
- 07:xx — `readwise_to_kortex.py` (no flag) routes newsletters to per-domain `kortex_import/` folders.

## Weekly (Mondays)
- 12:xx — `ingest_kortex_exports.py --domain japanese` routes the past week's Kortex exports.
  Runs `build_wiki.py --domain japanese` and `wiki_lint.py --domain japanese` afterwards.
- 20:xx — Drain queue: `drain_youtube_queue.py --domain japanese` followed by Claude session
  using notebooklm-mcp to push URLs into NotebookLM.
- 09:xx — Telegram nudge: "Export the past week's Kortex artefacts."

## Manual interventions
- Add a creator: append to `creators_seed.japanese.json`, run
  `resolve_youtube_channel_ids.py --domain japanese`, then re-run this script.
- Tune taxonomy: edit `taxonomies/japanese.py`, re-run `build_wiki.py --domain japanese`.
- Investigate routing: see `kortex_import/japanese/` and `pending_youtube_imports.japanese.json`.
