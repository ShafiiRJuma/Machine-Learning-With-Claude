# Scenario 05 — Exam Results Processor
**Setting:** You're helping a lecturer at UDSM process end-of-semester exam results for a class. Each student has multiple scores, and the lecturer needs per-student summaries plus a class-wide overview.

### The raw inputs
```python
students = [
    {"name": "Amani Joseph", "scores": [78, 65, 82]},
    {"name": "Neema Kessy", "scores": [45, 50, 38]},
    {"name": "Salum Hamisi", "scores": [90, 88, 95]},
    {"name": "Grace Mtei", "scores": [60, 55, 70]}
]
```

### What you must build — 2 functions

**1. `calculate_average(scores)`**
- Input: a list of numbers
- Returns the average (float), calculated using a **loop with a running tracker** — not `sum(scores)/len(scores)`
- Must **return** the value, not print it

**2. `process_students(students)`**
- Input: the `students` list
- For each student:
  - Calculate their average using `calculate_average()` (don't re-write the averaging logic inline)
  - Determine `"pass"` if average is **50 or above**, else `"fail"`
- Returns a list of dictionaries, one per student, in this exact shape:
  ```python
  {"name": "Amani Joseph", "average": 75.0, "result": "pass"}
  ```
- Also loop through the returned list and print each student's summary line in this exact style:
  ```
  Amani Joseph: 75.00 - pass
  ```

### Expected output
```
Amani Joseph: 75.00 - pass
Neema Kessy: 44.33 - fail
Salum Hamisi: 91.00 - pass
Grace Mtei: 61.67 - pass
```

### Rules
- `calculate_average` must use a **loop with a running tracker** to sum, then divide by `len(scores)` — no `sum()`
- `process_students` must call `calculate_average()` internally for each student — don't recompute it inline
- Average in the printed summary must be formatted to **2 decimal places**
- The `"average"` value stored in the returned dictionary can be the raw float (unrounded) — only the **printed** version needs `.2f` formatting

Give it your best shot.
