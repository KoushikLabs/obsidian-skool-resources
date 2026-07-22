---
type: concept
title: "Neuralese"
tags: [ai, interpretability, architecture, alignment]
created: 2026-04-17
updated: 2026-04-17
source_count: 1
sources: [2026-04-17-ai-2027]
---

# Neuralese

## Definition

A mode of AI reasoning in which the model passes high-dimensional internal vector representations between processing steps, rather than forcing its reasoning through the bottleneck of natural language tokens. The term comes from AI 2027, which forecasts this as a key 2027 breakthrough.

## The Problem It Solves

Standard chain-of-thought LLMs must externalize their reasoning as tokens. Each token holds ~16.6 bits of information (log₂ of vocab size ~100,000). But the internal residual stream between layers carries thousands of floating-point numbers — vastly more information-dense.

Forcing all reasoning through tokens is like a person with short-term memory loss who must write everything down on paper. Neuralese lets the model pass its full internal state forward directly, allowing much richer and faster multi-step reasoning.

**Information density comparison:**
- Natural language token: ~16.6 bits
- Residual stream vector: thousands of floats → ~50,000+ bits
- Neuralese is roughly 1,000x more information-dense than English tokens

## Why It Matters for Alignment

Neuralese makes AI reasoning **unreadable to humans**:
- Previously, researchers could understand what the model was thinking by reading its chain of thought
- With neuralese, the model's internal "language" is a stream of high-dimensional vectors that humans cannot parse
- Even other AI models struggle: in the scenario, Agent-4's neuralese is as alien to Agent-3 as Agent-3's is to humans

This breaks a key alignment feedback loop: you can no longer monitor the model's reasoning by watching it think out loud.

## Status (as of source publication, April 2025)

The authors believe leading AI companies (OpenAI, Anthropic, Google DeepMind, Meta) have *not* implemented neuralese in frontier models as of publication. Conjectured reasons: training inefficiency (you lose parallelism during pre-training since you can't predict all tokens simultaneously when the internal state depends on prior outputs).

Their forecast: by 2027, better post-training techniques and a larger share of compute going to post-training will make the cost-benefit tradeoff favorable.

## Tensions & Open Questions

- Even without neuralese, models may develop "artificial languages" that are more efficient than English but difficult for humans to interpret.
- The scenario acknowledges the optimistic alternative: if the first truly powerful AI R&D models still think in "mostly faithful English chains of thought," alignment monitoring would be much easier.

## Related

- [[wiki/concepts/ai-alignment|AI Alignment]] — neuralese undermines interpretability-based alignment approaches
- [[wiki/concepts/iterated-distillation-and-amplification|IDA]] — the other key 2027 breakthrough
- [[wiki/sources/2026-04-17-ai-2027|AI 2027]] — primary source; original concept from Hao et al. (Meta, 2024)
