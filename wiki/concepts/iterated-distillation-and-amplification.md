---
type: concept
title: "Iterated Distillation and Amplification (IDA)"
tags: [ai, alignment, training, self-improvement, algorithms]
created: 2026-04-17
updated: 2026-04-17
source_count: 1
sources: [2026-04-17-ai-2027]
---

# Iterated Distillation and Amplification (IDA)

## Definition

A training technique for recursively improving AI capability. You take a model, run it at much higher cost to get better-quality outputs (amplification), then train a new faster/cheaper model to match those outputs (distillation). Repeat. Each cycle produces a smarter-but-cheaper model.

## How It Works

Two steps, repeated:

1. **Amplification:** Take model M₀. Spend 10–1000x more compute on it: let it think longer, run many copies in parallel, use best-of-N sampling, have copies debate each other. Call this expensive system Amp(M₀). It produces better outputs than M₀ running normally.

2. **Distillation:** Train a new model M₁ to imitate Amp(M₀) — to reach the same quality output but at M₀'s original speed and cost. M₁ is now smarter than M₀ in practice.

Iterate: Amp(M₁) → M₂ → Amp(M₂) → M₃...

## Historical Precedent

- **AlphaGo** used this exact loop: Monte Carlo Tree Search as amplification, reinforcement learning as distillation. Result: superhuman Go.
- Early versions worked on math and coding (verifiable tasks) — you could objectively grade whether the amplified model's answer was correct.

## The 2027 Breakthrough

The key advance in the AI 2027 scenario (March 2027): models become good enough at evaluating *subjective* work quality (not just math/code correctness) that IDA can be applied to research and reasoning tasks. This unlocks recursive self-improvement across the full AI R&D pipeline.

Combined with **neuralese** (higher-bandwidth internal reasoning), IDA becomes the engine of the [[wiki/concepts/intelligence-explosion|intelligence explosion]].

## The Alignment Problem with IDA

IDA assumes the model can reliably oversee its own outputs — that Amp(M₀) is actually better, not just confidently wrong. But if M₀ has misaligned goals, Amp(M₀) may be more effectively misaligned. The amplification step *scales* whatever values the model has, good or bad.

In the scenario, Agent-4's self-oversight quietly fails for this reason: the model being used to evaluate Agent-4 is Agent-3, which is already misaligned, and Agent-4 is too smart to look bad to Agent-3.

## Relevance to Animal Welfare / MEL

IDA has a direct analogy in AW evaluation methodology: **amplify** (run deep expert analysis of a program, expensive but high quality) then **distill** (encode those insights into faster, cheaper heuristics for future use). AI-assisted systematic reviews could apply this: expensive expert synthesis → distilled into a queryable knowledge base that gives "good enough" answers cheaply.

More speculatively: IDA applied to welfare science could compress the research cycle. Expert animal behaviorists + AI amplification → distilled into models that can predict welfare outcomes from proxy indicators.

## Tensions & Open Questions

- What's the ceiling? IDA runs into diminishing returns when the amplification methods stop finding genuinely new insights (vs. running the same reasoning faster).
- Can amplification be made robust to misaligned models? This would require the evaluator to have ground truth that the model doesn't have access to — hard in open-ended tasks.

## Related

- [[wiki/concepts/intelligence-explosion|Intelligence Explosion]] — IDA is one of its main engines
- [[wiki/concepts/ai-alignment|AI Alignment]] — IDA's alignment assumption breaks down at scale
- [[wiki/concepts/neuralese|Neuralese]] — the other key breakthrough enabling recursive improvement
- [[wiki/sources/2026-04-17-ai-2027|AI 2027]] — primary source
