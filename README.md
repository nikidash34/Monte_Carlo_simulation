# When Importance Sampling Fails: Rare-Event Estimation for Heavy-Tailed Insurance Losses

A case study on the Danish Fire Insurance dataset, exploring why a standard variance-reduction technique breaks down for heavy-tailed risk.

## Summary

This project fits a Pareto model to real insurance claim severities and uses Monte Carlo simulation to estimate the probability of extreme aggregate annual losses. The naive estimator converges prohibitively slowly in the tail, which motivates importance sampling as a variance-reduction technique. However, a claim-level Pareto-tilting approach — while theoretically unbiased — is shown to fail in practice due to **weight collapse**, quantified by an effective sample size below 1%.

## What's inside

- Tail-index estimation via both a curve-fit MLE and the Hill estimator, with a comparison of their bias in the extreme tail
- A compound Poisson–Pareto model for aggregate annual losses (the standard actuarial collective risk model)
- A convergence analysis showing how estimator variance scales with the rarity of the event
- An importance sampling implementation with likelihood-ratio reweighting and effective sample size (ESS) diagnostics
- A goodness-of-fit check (QQ-plot) against the fitted Pareto model

## Running it

```bash
pip install -r requirements.txt
jupyter notebook main.ipynb
```

Run the notebook from the repository root — it loads `danish_fire_insurance.csv` via a relative path.

## Data

`danish_fire_insurance.csv` — a classic heavy-tailed loss dataset used in the actuarial literature (large fire insurance claims, Denmark).
