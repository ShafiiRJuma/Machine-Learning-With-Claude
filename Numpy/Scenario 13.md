# Scenario 13 — Outlier Detector
**Setting:** A microfinance institution in Mwanza tracks daily loan repayment amounts. Some repayments look suspicious — either unusually small (possible fraud/error) or unusually large (needs manual review). You need to flag and extract these outliers automatically.

### What it is (quick theory before we build)
**Boolean indexing** lets you use a `True`/`False` array to *filter* another array — pulling out only the elements where the condition is `True`. **Fancy indexing** means using an array of indices (or a boolean mask) directly inside `[...]` instead of a single number or slice.

### Why it matters for Data Science
This is the NumPy equivalent of Pandas' `df[df['amount'] > 1000]` — filtering rows based on a condition. It's one of the most-used operations in real data cleaning: finding bad data, extracting a subset, flagging anomalies.

### How it works — minimal example
```python
import numpy as np

values = np.array([10, 200, 15, 5000, 30])
mask = values > 100          # [False True False True False]
outliers = values[mask]      # [200 5000] — only the elements where mask is True
print(outliers)
```
You can also combine conditions with `&` (and) / `|` (or) — but each condition needs its own parentheses:
```python
mask = (values > 20) & (values < 1000)
```

### The mistake everyone makes
Using Python's `and`/`or` instead of `&`/`|` with NumPy arrays — `and`/`or` don't work element-wise and will throw an error. Also forgetting the parentheses around each condition when combining them.

---

## The scenario

### The raw inputs
```python
import numpy as np

repayments = np.array([45000, 50000, 2000, 48000, 500000, 47000, 1000, 52000, 49000, 300000])
# Daily loan repayments in TZS across 10 transactions
```

### What you must build
Plain script, using boolean/fancy indexing (no loops):

1. `low_outliers` — repayments **below** 5000 TZS (extract the actual values, not just True/False)
2. `high_outliers` — repayments **above** 200000 TZS
3. `normal_range` — repayments that are **both** ≥ 5000 AND ≤ 200000 (use `&` with parentheses around each condition)
4. `outlier_count` — total number of outliers (low + high combined) — use `.size` or `len()` on your outlier arrays
5. Print all in this exact style:

```
Low Outliers: [2000 1000]
High Outliers: [500000 300000]
Normal Range: [45000 50000 48000 47000 52000 49000]
Outlier Count: 4
```

### Rules
- No `for` loops or manual `if` checks — pure boolean/fancy indexing
- Use `&` (not `and`) for combining conditions, with parentheses around each side
- `outlier_count` must be derived from the lengths of `low_outliers` and `high_outliers`, not hardcoded

Give it a try — send your code.
