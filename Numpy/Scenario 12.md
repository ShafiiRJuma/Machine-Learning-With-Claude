# Scenario 12 — Student Performance Stats
**Setting:** Back to the UDSM lecturer's exam score matrix — but now they want summary statistics: per-student averages, per-exam averages, and how spread out the scores are (standard deviation), all computed in one shot across the whole class.

### What it is (quick theory before we build)
NumPy aggregation functions (`.sum()`, `.mean()`, `.std()`) can work on a whole array, or on just one **axis** (direction) of a 2D array. `axis=0` collapses down the **rows** (giving one result per column). `axis=1` collapses across the **columns** (giving one result per row).

### Why it matters for Data Science
This is exactly the operation behind `df.mean()` vs `df.mean(axis=1)` in Pandas — "average per column" (e.g., average score per exam) vs. "average per row" (e.g., average score per student). Getting `axis` right here means Pandas won't feel confusing later.

### How it works — minimal example
```python
import numpy as np

grid = np.array([
    [10, 20],
    [30, 40],
])
print(grid.mean())          # 25.0 → overall average of all 4 numbers
print(grid.mean(axis=0))    # [20. 30.] → average DOWN each column (10+30)/2, (20+40)/2
print(grid.mean(axis=1))    # [15. 35.] → average ACROSS each row (10+20)/2, (30+40)/2
```

A useful way to remember it: `axis=0` moves *down* the rows (column-wise result), `axis=1` moves *across* the columns (row-wise result).

### The mistake everyone makes
Mixing up `axis=0` and `axis=1` — always double check by counting how many results you got back (should match the number of columns for `axis=0`, or number of rows for `axis=1`).

---

## The scenario

### The raw inputs
```python
import numpy as np

scores = np.array([
    [78, 65, 82],   # Editha
    [45, 50, 38],   # Godfrey
    [90, 88, 95],   # Consolata
    [40, 35, 42],   # Peter
])
# Rows = students (Editha, Godfrey, Consolata, Peter), Columns = Exam1, Exam2, Exam3
```

### What you must build
Plain script, using aggregation functions with the correct `axis`:

1. `student_averages` — average score **per student** (one value per row) — round to 2 decimal places using `np.round()`
2. `exam_averages` — average score **per exam** (one value per column) — round to 2 decimal places
3. `overall_std` — standard deviation of **all** scores combined (no axis — whole array), round to 2 decimal places
4. `highest_exam_avg_index` — the index (0, 1, or 2) of the exam with the **highest** average, using `np.argmax()` on `exam_averages`
5. Print all four in this exact style:

```
Student Averages: [75.   44.33 91.   39.  ]
Exam Averages: [63.25 59.5  64.25]
Overall Std: 20.94
Highest Average Exam Index: 2
```

### Rules
- Use `.mean(axis=...)` with the correct axis for each — think carefully about which axis collapses which direction
- Use `.std()` for standard deviation, `np.argmax()` for the index of the max value
- Round using `np.round(array_or_value, 2)`

Take your time on the axis choice — it's the trickiest part of this scenario. Send your code when ready.
