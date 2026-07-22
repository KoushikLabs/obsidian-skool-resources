---
type: concept
title: "AI Capability Milestones"
tags: [ai, agi, forecasting, benchmarks]
created: 2026-04-17
updated: 2026-04-17
source_count: 1
sources: [2026-04-17-ai-2027]
---

# AI Capability Milestones

## Definition

A framework for tracking AI capability progress using discrete, operationalizable milestones. Each milestone represents a qualitative shift in what AI can do, rather than a benchmark score. The AI 2027 scenario defines four milestones on the path from today to superintelligence.

## The Four Milestones (AI 2027 Framework)

| Milestone | Abbreviation | Definition | Scenario Date |
|-----------|-------------|------------|---------------|
| **Superhuman Coder** | SC | Can do any coding task the best human AI engineer can do, but faster and cheaper enough to run many copies | March 2027 |
| **Superhuman AI Researcher** | SAR | Same as SC but for *all* cognitive AI research tasks (including research taste, experiment design, etc.) | August 2027 |
| **Superintelligent AI Researcher** | SIAR | Vastly better than the best human researcher at AI research | November 2027 |
| **Artificial Superintelligence** | ASI | Much better than the best human at *every* cognitive task | December 2027 |

The SC → ASI gap is ~9 months in the scenario's "race" ending.

## What Makes This Framework Useful

Unlike "AGI" (which means different things to different people), these milestones are operationalizable:
- **SC** has a measurable proxy: the length of coding tasks AI can handle with 80% reliability. METR research (2025) found this "time horizon" doubled every 7 months from 2019–2024, accelerating to every 4 months after 2024.
- Each milestone has a concrete capability implication for AI R&D automation (which drives the [[wiki/concepts/intelligence-explosion|intelligence explosion]]).

## Why the Gap Compresses

The interval between milestones shrinks not because AI improves faster in absolute terms, but because AI is accelerating its *own* training:

- SC enables 4x faster algorithmic progress
- SAR enables 10x → 50x
- At 50x, a week of research = a year of human-paced progress

So SIAR and ASI arrive nearly simultaneously with SAR in calendar time, even though in "subjective AI-time" there may be years between them.

## Relevance to Animal Welfare / MEL

The milestone framework helps AW practitioners calibrate *when* AI tools will be useful for which problems:

- **Today (pre-SC):** LLMs are already useful for evidence synthesis, report drafting, document analysis, monitoring dashboards. High feasibility for AW applications now.
- **SC era (~2027):** Automated research pipelines, on-demand systematic reviews, more reliable agentic monitoring systems.
- **SAR era (~2028+):** AI that can actually run the research cycle for animal welfare science questions — what interventions work, why, for which species in which contexts. This could compress the AW evidence base dramatically.

The implication: AW orgs should be building AI capacity now (to use current tools), while planning for dramatically more capable tools within a few years.

## Tensions & Open Questions

- **Compute as the binding constraint:** By the SC stage, the bottleneck is no longer research quality but available compute to run experiments. This means the multiplier plateaus around 50x regardless of how smart the model is.
- **"Research taste" as the last moat:** The scenario treats high-level research direction as hard to automate — the last place humans add value. This is empirically uncertain.
- **SC median may be later than 2027:** The authors note that adjusting for "outside of model factors" pushed their median to ~2030, though 2027 remains a serious possibility.

## Related

- [[wiki/concepts/intelligence-explosion|Intelligence Explosion]] — milestones are checkpoints along the explosion curve
- [[wiki/concepts/ai-alignment|AI Alignment]] — alignment gets harder at each milestone
- [[wiki/sources/2026-04-17-ai-2027|AI 2027]] — primary source; see also ai-2027.com/supplements/timelines-forecast
