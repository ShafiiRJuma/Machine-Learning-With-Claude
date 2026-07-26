# Scenario 14 — Grade Normalizer
**Setting:** You're helping a UDSM department compute a **weighted final grade** for students, where each exam counts differently toward the final mark (e.g., final exam counts more than a quiz). This is your first taste of linear algebra — the dot product is exactly how weighted sums are computed in real ML models (it's literally how a neural network layer works).

### What it is (quick theory before we build)
The **dot product** of two vectors multiplies matching elements together, then sums the results. `np.dot(a, b)` (or `a @ b`) does this in one step. The **norm** (`np.linalg.norm()`) measures the "length" or magnitude of a vector — useful for things like measuring how far a set of scores is from a reference point.

### Why it matters for Data Science
A weighted average — exactly what you're about to compute — is a dot product. This exact operation, scaled up to millions of numbers, is the core computation inside every linear regression model and every layer of a neural network.

### How it works — minimal example
```python
import numpy as np

scores = np.array([80, 90, 70])
weights = np.array([0.5, 0.3, 0.2])

weighted_total = np.dot(scores, weights)
# = (80*0.5) + (90*0.3) + (70*0.2) = 40 + 27 + 14 = 81.0
print(weighted_total)   # 81.0

vector = np.array([3, 4])
print(np.linalg.norm(vector))   # 5.0  → sqrt(3^2 + 4^2)
```

### The mistake everyone makes
Using `*` (element-wise multiply) when they actually want `np.dot()` (multiply-then-sum) — `*` gives you back an array, not a single combined number.

---

## The scenario

### The raw inputs
```python
import numpy as np

students = ["Editha", "Godfrey", "Consolata", "Peter"]
scores = np.array([
    [78, 65, 82],   # Editha: Quiz, Midterm, Final
    [45, 50, 38],   # Godfrey
    [90, 88, 95],   # Consolata
    [40, 35, 42],   # Peter
])
weights = np.array([0.2, 0.3, 0.5])   # Quiz 20%, Midterm 30%, Final 50%
```

### What you must build
Plain script (no loops — use dot product and vectorized operations):

1. `final_grades` — the weighted final grade for **every student at once**, using `np.dot(scores, weights)` — this works directly on the whole 2D matrix against the 1D weights vector, giving one weighted result per student
2. `final_grades_rounded` — same as above, rounded to 2 decimal places
3. `top_student_index` — index of the student with the highest final grade, using `np.argmax()`
4. `top_student_name` — use `top_student_index` to look up the name from the `students` list
5. `score_vector_norm` — the `np.linalg.norm()` of Consolata's raw score vector (row index 2) — a measure of her overall score "magnitude"
6. Print in this exact style:

```
Final Grades: [76.1  44.9  91.9  39.5 ]
Top Student: Consolata (Grade: 91.9)
Consolata's Score Vector Norm: 152.24
```

### Rules
- Use `np.dot(scores, weights)` for the whole matrix at once — don't loop per student
- `top_student_name` comes from indexing the plain Python list `students`, not the NumPy array
- Round `score_vector_norm` to 2 decimal places too

Give it a try — this ties together everything from Module 2.
