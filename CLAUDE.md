# Japanese Teachings Wiki — Schema (multi-creator)


This vault is a Karpathy-style LLM Wiki: persistent, compounding, LLM-maintained.
Multiple AI content creators coexist under `creators/`. Concepts and entities are
shared across creators so you see which ideas/tools show up in whose content.

## Layout
```
creators/{slug}/
  profile.md              hand-editable: channel URL, community URLs, NotebookLM notebook URL,
                          kortex_notebook_title (used to route Kortex exports)
  raw/{resource-slug}/    immutable downloaded artefacts (PDFs, n8n JSONs, …). Never modify.
  wiki/
    sources/{date}-{slug}.md   one page per ingested source (video + bundle)
    chats/{date}-{slug}.md     Kortex-exported NotebookLM chat transcripts
    studio/{date}-{slug}.md    Kortex-exported NotebookLM studio notes
    audio/{date}-{slug}.md     Kortex-exported audio overview transcripts

wiki/
  concepts/{slug}.md      SHARED across creators (RAG, Agentic Workflows, …)
  entities/{slug}.md      SHARED across creators (Anthropic, n8n, Vapi, …)

index.md, log.md, overview.md, CLAUDE.md   at vault root
```

## Frontmatter conventions
**Source page (video + bundle):**
```yaml
---
title: "..."
date: YYYY-MM-DD
creator: <slug>
youtube: <url>
source_url: <url>
type: source
concepts: [slug1, slug2]
entities: [slug1, slug2]
---
```

**Concept / entity page:**
```yaml
---
title: <Display Name>
type: concept           # or "entity"
sources: <count>
---
```

**Creator profile (`creators/{slug}/profile.md`):**
```yaml
---
name: <Display Name>
slug: <slug>
youtube: <url>
communities:
  - <community url 1>
  - <community url 2>
notebooklm_notebook: <url>
kortex_notebook_title: <string used by Kortex to name exports>
---
```

## Wikilink style
Use **bare-filename** wikilinks (`[[rag]]`, `[[2026-01-05-...]]`) — NOT relative paths.
Obsidian resolves them globally by filename. This keeps links unbroken when files move.

## Workflows

### Ingest a new creator
1. Create `creators/{slug}/profile.md` with at minimum `name`, `youtube`, `communities`, and a blank `notebooklm_notebook`.
2. User joins the free community manually (signup required; not something the LLM can do).
3. User pastes the NotebookLM notebook URL + Kortex export title into `profile.md`.
4. LLM runs the appropriate scraper (Skool/Circle/generic), writing raw files to `creators/{slug}/raw/{resource-slug}/`.
5. `build_wiki.py` is re-run. It rebuilds source pages, aggregates cross-refs, preserves Notes sections.

### Ingest a new source for an existing creator
Drop the file(s) into `creators/{slug}/raw/{new-resource-slug}/` (or re-run the scraper).
Add a row to the creator's source-data file if the wiki uses one (e.g. Nate Herk uses `sheet_data.json`).
Re-run `build_wiki.py`.

### Ingest Kortex NotebookLM exports
1. In Kortex Pro, set up an export pipeline per notebook that sends chats / studio notes / audio transcripts to `%USERPROFILE%\Downloads\Kortex\` (or any fixed folder).
2. Run `ingest_kortex_exports.py`. It:
   - Matches filenames against each creator's `kortex_notebook_title` in `profile.md`.
   - Routes to `creators/{slug}/wiki/chats|studio|audio/{date}-{slug}.md` with normalised frontmatter.
3. Run `build_wiki.py`. Concept/entity pages pick up backlinks from the new files (marked 💬 chat / 📝 studio / 🎧 audio).

### Answer a query
Read `index.md` first to find candidate pages; read concept/entity pages; synthesise with `[[wikilinks]]` to cited pages. If the answer represents new synthesis worth keeping, file it under `wiki/analyses/{date}-{slug}.md` and `grep` the log convention when appending.

### Lint pass
- Concept/entity pages with zero backlinks: propose merge or deletion.
- Sources mentioning a concept that doesn't yet have a page: propose creation (extend `CONCEPTS_TAX` in `build_wiki.py`).
- Contradictions across sources (`n8n is dying` vs `n8n is the best tool`): record under the relevant concept's `## Notes` as a Tensions subsection.

## Hand-curation & Notes preservation
**`## Notes` sections in concept / entity pages and in `overview.md` are HAND-EDITABLE and preserved across rebuilds.** `build_wiki.py` detects the `## Notes` heading and keeps everything from there down verbatim. Everything *above* `## Notes` (frontmatter, backlink lists, headers) is regenerated.

Do not put hand-written content above the `## Notes` heading — it will be overwritten.

## Scripts (at `C:\Users\kousa\Desktop\Claude code\`)
- `build_wiki.py` — rebuild everything. Idempotent. Migrates legacy layout on first run.
- `ingest_kortex_exports.py` — route Kortex downloads into the correct creator folder.
- (future) `discover_communities.py`, `scrape_skool.py`, `scrape_circle.py`, `scrape_generic.py`, `prepare_for_notebooklm.py`.

## Taxonomy
`CONCEPTS_TAX` and `ENTITIES_TAX` live in `taxonomies/{domain}.py` (one file per pipeline domain). Extend them as new creators introduce new tools/concepts — add a `(slug, display_name, regex)` tuple and re-run `build_wiki.py --domain {domain}`.
