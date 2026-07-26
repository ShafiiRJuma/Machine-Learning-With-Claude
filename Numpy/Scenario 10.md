
# Module 2 — NumPy

Quick shift in gears here. Everything so far has been pure Python — lists, loops, dicts. NumPy introduces the **array**, a completely different data structure built for fast, bulk numerical operations. This is the foundation Pandas is built on top of, so getting comfortable here pays off immediately in Module 3.

### What it is
A NumPy array (`ndarray`) is like a list, but every element must be the **same type**, and it's stored in memory in a way that lets you do math on the *whole array at once* — no loops needed.

### Why it matters for Data Science
When you load a spreadsheet of 10,000 exam scores, you don't want to write a `for` loop to add 5 bonus points to every score. With NumPy, you just write `scores + 5` and it applies to all 10,000 instantly. This is called **vectorization**, and it's the difference between code that takes 2 seconds vs. code that takes 2 minutes on real datasets.

### How it works — minimal example
```python
import numpy as np

scores = np.array([78, 65, 82, 90])
print(scores.shape)   # (4,)  → 4 elements, 1 dimension
print(scores.dtype)   # int64 → all elements are integers

matrix = np.array([[78, 65], [82, 90]])
print(matrix.shape)   # (2, 2) → 2 rows, 2 columns
print(matrix[0, 1])   # 65 → row 0, column 1
```

### The mistake everyone makes
Mixing types inside one array without realizing NumPy silently converts everything:
```python
np.array([1, 2, "3"])   # all become strings! dtype becomes '<U21'
```

---

# Scenario 10 — Exam Score Matrix
**Setting:** You're back helping the same UDSM lecturer, but now for a bigger class with multiple exams. Instead of separate lists per student, the data comes in as a **grid** — rows are students, columns are exams.

### The raw inputs
```python
import numpy as np

scores = np.array([
    [78, 65, 82],   # Editha
    [45, 50, 38],   # Godfrey
    [90, 88, 95],   # Consolata
    [40, 35, 42],   # Peter
])
```
Rows = students (in order: Editha, Godfrey, Consolata, Peter). Columns = exams (Exam1, Exam2, Exam3).

### What you must build
Plain script (no functions needed yet — this scenario is about getting comfortable with array basics):

1. Print the **shape** of `scores` (should show 4 rows, 3 columns)
2. Print the **dtype** of `scores`
3. Get **Godfrey's scores** (the whole second row) using indexing — store in a variable `godfrey_scores`
4. Get **everyone's Exam2 score** (the whole second column) using indexing — store in a variable `exam2_scores`
5. Get **Consolata's Exam3 score** specifically (one single value) using indexing — store in a variable `consolata_exam3`
6. Print all of the above with labels, in this exact style:

```
Shape: (4, 3)
Dtype: int64
Godfrey's scores: [45 50 38]
Exam 2 scores: [65 50 88 35]
Consolata's Exam 3 score: 95
```

### Rules
- Use `.shape` and `.dtype` — don't hardcode the numbers
- Use NumPy indexing (`array[row]`, `array[:, col]`, `array[row, col]`) — not Python list-style loops
- Row/column indices are 0-based, same as regular Python lists

Give it a try — send your code.
