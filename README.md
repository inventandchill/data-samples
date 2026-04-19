# Data samples

Training-ready matrix for pump.fun 5x-in-3h prediction.

- `b_prime_training_matrix.csv` / `.pkl` / `.xlsx` — 3231 rows × 76 columns
  - 75 feature columns (numeric)
  - 1 target column `target_3h_5x_h` (binary)
  - Base rate: 11.05% (357 positives)
- Tokens migrated 2026-04-02 to 2026-04-17
- All features computed on `[first_trade, migration_time + 60s]`
- Target: `x_max_excl_top1 >= 5` in `[mig+60s, mig+60s+3h]` (disjoint from feature window)

Feature groups: 57 iter-12 base features, 17 EXT_A features (drafts1-style), 1 Hurst exponent.

## Feature research notebook

`feature_research.ipynb` — comprehensive univariate analysis of all 75 features vs the continuous target `x_excl_top1_3h_h` (raw x-multiple, not binary 5x target).

Methodology (6 metrics per feature):
1. Spearman correlation
2. Pearson correlation on log(1+target)
3. Decile monotonicity R² (median-per-bin linear fit)
4. MSE reduction on best binary split (regression tree Gini equivalent)
5. Top vs bottom decile log-median lift
6. Top-decile P(target ≥ 5) — practical precision

Plus hypothesis tests (binomial test vs base rate), non-monotonic detection (quadratic benefit), and correlation heatmap across top features.

Artefacts:
- `feature_research.ipynb` — executed notebook with plots inline
- `feature_influence_ranked.csv` — 75 features ranked by combined score
- `top10_features.png` — decile + scatter plots for top 10
- `top15_correlation.png` — Spearman correlation heatmap among top 15
- `top15_top_decile_5x_rate.png` — practical 5x-rate per feature
- `nonmonotonic_top5.png` — features with non-linear patterns
