# Fair threshold modification for deep-learning crash prediction

A reproduction of the threshold-modification method of Chen, Xu and Peeta
(2025), *Transportation Research Part B*, applied to FARS 2016–2018 crash data.

The method assigns each sensitive group its own decision threshold so that the
difference in per-group accuracy is no longer statistically significant under a
two-proportion z-test, without retraining the model.

`fair_threshold_fars.ipynb` runs the whole pipeline: data preparation, the
neural network, the default-threshold baseline, Subproblem (5)–(7) solved by
both exhaustive search and the MILP reformulation (9)–(14), the Equation (8)
target accuracy, threshold identification, and the final comparison. Two
pairings are examined: urban vs. rural, and drivers under 30 vs. 30 and over.

The seed is fixed (`set_random_seed(42)`), so the results reproduce exactly.
They are reported in the accompanying write-up.

## Implementation

The paper gives the problem and its MILP reformulation as formulations, not as
code. I worked out the decision variables and constraints myself and solved the
MILP with CBC via PuLP. The exhaustive search is included as an independent
check; both return the same optimal accuracy for all four groups.

## Running it
