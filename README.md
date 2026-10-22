# econ5200-lab07-bootstrapping
# Diagnosing Broken Confidence Intervals

## Objective

I examined why nominal 95% confidence intervals can give misleading results for discrete statistics, skewed data, and clustered observations.

## Methodology

- I bootstrapped the median age from 32,561 observations and checked the percentile and BCa intervals.
- I ran 400 simulations of skewed data with samples of 50, comparing parametric and bootstrap interval coverage for the mean and median.
- I simulated wages across 25 firms and compared resampling individual workers with resampling entire firms.
- I ran `bootstrap_utils.py` for percentile, i.i.d., and cluster bootstrap methods.
- I revised an AI-generated coverage function to use consistent trial seeds and checked its results against my earlier simulation.

## Key Findings

- The median-age bootstrap had a standard error of **0.000000**. BCa returned `nan` with a warning, showing that a zero-width interval does not establish certainty.
- For the mean, coverage was **92.5%** with the parametric interval and **92.0%** with the bootstrap interval. For the median, coverage was **66.8%** and **92.8%**, respectively, against a nominal **95%** standard.
- Resampling entire firms produced an interval **5.7 times wider** than resampling workers individually. Naive coverage was only **19.5%**, while cluster-bootstrap coverage was **91.0%**.
- After I revised the AI prompt to specify the trial seeds, the AI-generated function reproduced the **19.5%** and **91.0%** coverage results exactly.
