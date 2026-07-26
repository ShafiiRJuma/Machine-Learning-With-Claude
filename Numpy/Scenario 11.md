# Scenario 11 — Sales Data Transformer
**Setting:** You're helping a small electronics shop in Dar es Salaam that sells phones. They track daily sales in Tanzanian Shillings, but need to quickly apply price adjustments, currency conversions, and tax calculations across the whole dataset — without writing loops.

### What it is (quick theory before we build)
**Vectorization** means applying an operation to an entire array at once, instead of looping element by element. **Broadcasting** is what makes `array + 5` or `array * 2` work — NumPy automatically "stretches" the single number across every element.

### Why it matters for Data Science
This is the single biggest reason NumPy (and Pandas, which is built on it) is fast. A loop-based version of `prices * 1.18` over a million rows would take seconds; the vectorized version takes milliseconds.

### How it works — minimal example
```python
import numpy as np

prices = np.array([1000, 2000, 3000])
with_tax = prices * 1.18        # broadcasting: every element * 1.18
discounted = prices - 200       # every element - 200
print(with_tax)                 # [1180. 2360. 3540.]
```

### The mistake everyone makes
Writing a `for` loop to do this instead of trusting broadcasting:
```python
# Don't do this in NumPy:
result = []
for p in prices:
    result.append(p * 1.18)
```
This defeats the entire purpose of using NumPy in the first place.

---

## The scenario

### The raw inputs
```python
import numpy as np

daily_sales_tzs = np.array([150000, 320000, 89000, 410000, 265000])
# 5 days of phone sales, in Tanzanian Shillings
```

### What you must build
Plain script, using **only vectorized operations** (no loops):

1. `sales_with_tax` — apply 18% VAT to every day's sales (multiply by `1.18`)
2. `sales_usd` — convert every day's original sales (`daily_sales_tzs`, not the tax version) to USD, using an exchange rate of `1 USD = 2600 TZS` (divide by `2600`)
3. `discounted_sales` — apply a flat 5000 TZS discount to every day's original sales
4. `high_sales_days` — a **boolean array** showing `True`/`False` for each day, where sales (original) were above 200000 TZS — this uses broadcasting with a comparison operator, not `if`
5. Print all four, rounded to 2 decimal places where relevant, in this exact style:

```
Sales with Tax: [177000. 377600. 105020. 483800. 312700.]
Sales in USD: [57.69 123.08 34.23 157.69 101.92]
Discounted Sales: [145000 315000  84000 405000 260000]
High Sales Days: [False  True False  True  True]
```

### Rules
- No `for` loops anywhere — pure broadcasting/vectorized operations
- For `sales_usd`, round using `np.round(array, 2)` — rounds every element at once
- `high_sales_days` must be created using a direct comparison (`array > value`), which NumPy automatically turns into a boolean array

Give it a try — send your code.
