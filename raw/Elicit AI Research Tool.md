---
title: "Elicit: AI-Powered Research Assistant — How It Works"
source: "https://miracuves.com/blog/what-is-elicit-and-how-does-it-work/"
author: "Miracuves / Elicit (elicit.com)"
published: 2025
created: 2026-04-17
tags: ["clippings", "ai", "research-tools", "evidence-synthesis"]
---

# Elicit: AI-Powered Research Assistant

## What It Is

Elicit is an AI-powered research assistant platform that uses advanced language models to help users discover, organize, and synthesize information from academic literature. Developed by Ought. Searches over 138 million academic papers and 545,000 clinical trials from ClinicalTrials.gov.

Tagline: automates literature review — "turns what would normally be hours of manual work into a guided research workflow."

## How It Works (Step by Step)

1. **Query input:** User enters natural-language research question
2. **Source discovery:** System scans academic databases (primarily Semantic Scholar)
3. **Data extraction:** Pulls structured information — methods, sample size, outcomes, variables
4. **Synthesis:** Organizes results into comparison tables and summaries
5. **Refinement:** User filters, explores, exports findings

## Technical Architecture

- **LLMs:** Originally GPT-3; December 2025 integrated Claude Opus 4.5 (outperforms Gemini 3 Pro and GPT-5 on data extraction per internal evaluations)
- **Retrieval:** RAG (Retrieval-Augmented Generation) over Semantic Scholar indexed database — narrows hallucination risk by grounding in source documents
- **Extraction models:** Specialized models for pulling structured fields from papers
- **Cloud infrastructure:** Scalable processing

## Key Features

- Structured data extraction from papers (methods, outcomes, limitations)
- Evidence comparison tables across multiple studies
- Automated summarization and synthesis
- Citation transparency with source links
- Project-based workspaces for team collaboration
- Export to documents and spreadsheets
- Research Agents (released December 2025): complex workflows for broad topic exploration and research landscape mapping
- Systematic Review mode: human-level accuracy at fraction of cost/labor; synthesizes up to 80 papers in a single brief

## Accuracy Validation

- German Education Policy systematic review: 99.4% accuracy (1,502/1,511 data points correctly extracted)
- Cochrane comparison study (2025): compared against traditional literature searching across 4 case studies — generally comparable results with dramatically lower time investment

## Use Cases

- Academic researchers and graduate students
- Policy analysts and consultants  
- Healthcare and social science professionals
- Journalists (investigative research)
- **Directly relevant:** Evidence synthesis for program evaluation, systematic reviews of intervention effectiveness

## Pricing

- Free tier: basic research features
- Pro subscription: deeper search, advanced extraction
- Team/organization plans: shared workspaces
- Enterprise: custom deployments

## Why It Matters for AW/MEL

The platform directly addresses the "evidence synthesis" bottleneck in MEL practice. A version of this — or this tool itself — could be used by AW organizations to query what's known about intervention effectiveness, welfare science, or campaign strategy. The key limitation: Semantic Scholar focuses on academic literature; grey literature (org reports, program evaluations) would need a custom build or corpus addition.
