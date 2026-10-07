# Round 4 — Reconstruct

*Team:* BB-024  
*Queries used:* 64

## What we concluded

We reconstructed the Round 4 payment fraud screening system by
observing its output score and approval decision for different input
combinations.

The system returns a score between 0 and 1 and a decision of either
APPROVE or DECLINE.

In our observations, the latest recorded result was:

- *Score:* 0.9789
- *Decision:* APPROVE
- *Query:* R2 #16

The Round 4 input parameters included account balance, account age,
amount, beneficiaries, channel, linked cards, months active, recent
chargebacks, trust score, and utilisation.

## How we got there

We used repeated queries to observe how changes in the input parameters
affected the output score and decision.

A total of *64 queries* were recorded in our observations.

For the latest observation (R2 #16), the parameters that changed from
the previous query were:

- months_active
- recent_chargebacks
- utilisation

The resulting score was *0.9789, with an **APPROVE* decision.

## What we ruled out

We did not assign a definite effect to any single feature when multiple
features were changed at the same time.

In particular, the R2 #16 observation changed months_active,
recent_chargebacks, and utilisation together. Therefore, this
observation alone cannot establish which individual feature caused the
change in the output score.

## What we are still unsure about

The exact mathematical formula and internal decision boundary used by
the black-box system are still unknown.

Because multiple parameters can change between queries, additional
controlled experiments would be required to determine the exact
individual effect of each feature.

We also cannot conclude the exact relationship between every input
feature and the final score from the available observations alone.

## Reconstruction

Our goal was to use the collected black-box observations to build a
machine-learning approximation of the system.

The reconstruction uses the observed input parameters as features and
the black-box output score as the target.

The model can then be tested by comparing its predicted scores with
the scores returned by the black-box system.

## Conclusion

The collected observations show that the black-box system produces
different fraud-screening scores and decisions depending on the input
parameters.

Our latest observed case produced a score of *0.9789* and an
*APPROVE* decision.

The reconstruction is an approximation of the black-box behaviour,
rather than a claim that we know its exact internal implementation.
