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
