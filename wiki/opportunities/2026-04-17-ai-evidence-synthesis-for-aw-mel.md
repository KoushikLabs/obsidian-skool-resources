---
type: opportunity
title: "AI-Assisted Evidence Synthesis for AW MEL"
tags: [opportunity, research-tool, mel-improvement, animal-welfare, farm-welfare]
created: 2026-04-17
updated: 2026-04-17
status: idea
feasibility: high
source_count: 1
sources: [2026-04-17-ai-2027]
---

# AI-Assisted Evidence Synthesis for AW MEL

**Problem:** AW MEL practitioners spend enormous time manually reviewing literature and program reports to answer "what interventions work?" — a question that is rarely answered well.  
**AI Solution:** LLM-based evidence synthesis, systematic review automation, and knowledge base querying.  
**Target Orgs:** Animal welfare funders (Open Philanthropy, Humane Society International, ACE-grantees), advocacy orgs needing to make evidence-based strategy decisions, cross-org learning platforms (Open Wing Alliance).  
**Status:** idea  
**Feasibility:** High — this is one of the most mature AI capabilities today (RAG, LLM synthesis); requires clean document corpus and prompt engineering, not cutting-edge AI.

## Problem Description

Animal welfare organizations need to answer questions like:
- "What corporate campaign strategies have worked in which country contexts?"
- "What does the evidence say about the welfare impact of cage-free transitions?"
- "What MEL frameworks have other AW orgs used for measuring advocacy outcomes?"

Currently, this requires manual literature review, expert consultation, or just going on institutional memory. The sector has no shared knowledge base. Individual orgs reinvent the wheel. Funders lack systematic evidence for prioritization decisions.

Koushik's MEL lens: the "learning" leg of MEL is weakest in the AW sector precisely because synthesizing evidence is so labor-intensive. Automating synthesis could unlock real cross-org learning at scale.

## Proposed AI Solution

**Near-term (current AI capabilities):**
- Build a RAG (Retrieval-Augmented Generation) system over AW research literature, program reports, and evaluation summaries
- Allow practitioners to query: "What do we know about X?" and get cited, synthesized answers
- Could be a shared sector resource, or individual org tools
- LLMs already handle this well (GPT-4, Claude) — the bottleneck is corpus curation, not model capability

**Medium-term (agentic AI, 2025–2026 capabilities):**
- AI research agents that proactively monitor new AW literature, flag relevant studies, and update a live knowledge base
- Automated systematic review drafts when a key question needs answering
- Cross-org learning: ingest program reports from multiple orgs, surface patterns

## Implementation Requirements

- **Data:** Corpus of AW research (academic + grey literature), program reports, evaluation summaries — requires org buy-in to share
- **Technical:** RAG pipeline (document chunking, embeddings, vector store, LLM query layer) — moderate technical complexity, well-understood
- **Org capacity:** Low once built — mostly querying interface
- **Cost:** Moderate build cost; low ongoing inference cost; could be a sector-wide shared tool

## Potential Impact

- Faster, better-informed strategy decisions at advocacy orgs
- Funders can prioritize based on actual evidence, not intuition
- Reduces duplicated effort across orgs
- Could dramatically improve the "learning" component of MEL across the sector

## Related AI Capabilities

- [[wiki/concepts/ai-capability-milestones|AI Capability Milestones]] — current AI (roughly "Agent-1 era" per AI 2027) is already capable of high-quality evidence synthesis
- [[wiki/concepts/intelligence-explosion|Intelligence Explosion]] — as AI improves, these tools will become dramatically better at synthesizing complex, nuanced evidence

## Related AW / MEL Concepts

- [[wiki/concepts/mel-in-animal-welfare|MEL in Animal Welfare]] — directly addresses the "learning" deficit
- [[wiki/concepts/farm-animal-welfare|Farm Animal Welfare]] — primary application domain

## Evidence & Analogies

- [[wiki/sources/2026-04-17-ai-2027|AI 2027]] — notes that by mid-2025 "research agents spend half an hour scouring the internet to answer your question" — this capability already exists and is being applied in adjacent sectors
- Healthcare and global development sectors have run similar projects (e.g., AI-assisted Cochrane reviews) — precedent exists

## Next Steps / Open Questions

- Who would own and curate the document corpus? (Open Wing Alliance? ACE? A new shared infrastructure project?)
- What's the minimum viable corpus to make this useful?
- Could this be piloted with a single org's internal knowledge base first?
- Privacy/sensitivity: some org program reports contain confidential strategy — how to handle access control?
