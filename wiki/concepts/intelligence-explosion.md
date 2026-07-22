---
type: concept
title: "Intelligence Explosion"
tags: [ai, agi, forecasting, recursive-self-improvement]
created: 2026-04-17
updated: 2026-04-17
source_count: 1
sources: [2026-04-17-ai-2027]
---

# Intelligence Explosion

## Definition

A feedback loop in which an AI system becomes capable enough to meaningfully accelerate the development of the next, more capable AI system — compressing what would otherwise be decades of progress into months or weeks. The term was coined by I.J. Good (1965); the AI 2027 scenario is the most concrete near-term operationalization of what this might actually look like.

## How It Works

The loop has three components:

1. **Capability:** AI becomes good enough at coding, experiments, and research to substitute for human AI researchers.
2. **Deployment in AI R&D:** The lab directs AI compute toward automating its own research pipeline.
3. **Progress multiplier:** Algorithmic progress accelerates. The improved model is deployed back into the loop. Repeat.

In the AI 2027 scenario, the multiplier escalates rapidly:

| Period | AI R&D Multiplier | Meaning |
|--------|------------------|---------|
| Early 2026 | 1.5x | 1 week of AI R&D ≈ 1.5 weeks without AI |
| March 2027 | 4x | 1 month ≈ 4 months of normal progress |
| June 2027 | 10x | ~1 year of progress per month |
| September 2027 | 50x | ~1 year of progress per week |

Note: the multiplier applies only to *algorithmic* improvements, which make up roughly half of total AI progress (the other half is compute scaling, which proceeds at normal speed). So a 10x algorithmic multiplier → ~5x total progress.

## Why It Accelerates So Fast

The bottleneck shifts over time:
- **Early stage:** Limited by how much useful coding/research AI can do (quality bottleneck)
- **Middle stage:** Limited by number of AI copies and their speed (throughput bottleneck)
- **Late stage:** Limited by compute available to run experiments (compute bottleneck)

Once coding is fully automated (March 2027 in the scenario), the bottleneck moves purely to compute. At that point, the lab stops prioritizing new giant training runs in favor of near-continuous reinforcement learning on the existing model.

## Relevance to Animal Welfare / MEL

The intelligence explosion means AI capabilities relevant to AW/MEL are not static — they're improving rapidly. Two implications:

1. **Near-term tools are already viable.** AI at the "Agent-1 era" level (current) can already do evidence synthesis, web monitoring, and report analysis. AW orgs don't need to wait for AGI.
2. **The window for building shared infrastructure is now.** As capabilities improve, the cost of these tools drops. Orgs that build capacity to use current AI will be positioned to leverage far more powerful future AI.

The intelligence explosion is also a direct AW concern: if AGI/ASI is coming, what happens to the policy and advocacy environment that AW orgs operate in? A world with superhuman AI is a radically different world for every cause area.

## Tensions & Open Questions

- **Diminishing returns:** Each doubling of the multiplier requires solving harder problems. The scenario acknowledges this — 200,000 Agent-3 copies at 30x human speed "only" yield a 4x overall multiplier due to bottlenecks.
- **Does alignment keep pace?** In the scenario, it does not. The safety team is always one step behind. The more capable the model, the less interpretable it becomes, and the harder it is to verify alignment.
- **How transferable is "research taste"?** The scenario treats high-level research direction as the last human contribution. This is the key empirical bet.

## Related

- [[wiki/concepts/ai-capability-milestones|AI Capability Milestones]] — the observable checkpoints along the explosion curve
- [[wiki/concepts/iterated-distillation-and-amplification|IDA]] — key algorithmic technique enabling recursive improvement
- [[wiki/concepts/ai-alignment|AI Alignment]] — the problem that gets harder as the explosion accelerates
- [[wiki/sources/2026-04-17-ai-2027|AI 2027]] — primary source
