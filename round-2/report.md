# Round 2 — Investigate

*Team:* BB-024

*Queries used:* 16 / budget

## What we concluded

The system is a synthetic payment fraud screen that returns an approval score and an APPROVE/DECLINE decision. Our Round 2 experiments indicate that changes to multiple input features can substantially affect the approval score.

## How we got there

We ran controlled queries while changing selected features between queries. In Query 16, we changed months_active, recent_chargebacks, and utilisation. The resulting approval score was *0.9789 (APPROVE)*.

This provided evidence that these features are associated with meaningful changes in the model's output, although the experiment does not establish that any single feature alone caused the full score change.

## What we ruled out

Some feature changes produced very low approval scores and DECLINE decisions. This shows that not every increase or decrease in an input improves approval. We therefore avoided claiming a universal effect for individual features without stronger isolated evidence.

## What we are still unsure about

We are not yet certain about the independent causal effect or exact direction of every feature because several queries changed more than one feature at a time. More controlled one-feature-at-a-time experiments would be needed to establish individual effects with higher confidence.
