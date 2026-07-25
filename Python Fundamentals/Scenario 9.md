# Scenario 09 — Student Records System
**Setting:** You're building a small records system for a secondary school in Dodoma. The school wants to store each student as an object, then use list comprehensions to quickly generate reports — top performers, students needing support, and name lists — without writing long loops each time.

### What it is (quick theory before we build)
This scenario combines two things you already know separately: **classes** (Scenario 07) and **list comprehensions** (`[expr for item in list if condition]`, which you've used a few times already for stripping lines). Now you'll use a list comprehension to process a **list of objects**, pulling out attributes and filtering based on object state.

### Why it matters for Data Science
This is *exactly* the mental model behind Pandas. A `DataFrame` is basically a collection of "row objects" — and operations like `df[df['gpa'] > 3.5]['name']` are the vectorized version of exactly what you're about to build by hand.

---

## The scenario

### What you must build

**1. A `Student` class** with:
- `__init__(self, name, subject_scores)` — `subject_scores` is a dict, e.g. `{"Math": 78, "English": 65, "Physics": 82}`
- `average(self)` — returns the average of all values in `subject_scores`, calculated with a **loop + running tracker** (no `sum()`), same pattern as Scenario 05
- `is_passing(self)` — returns `True` if `average() >= 50`, else `False`

**2. A list of `Student` objects** (create these yourself, using this raw data):
```python
raw_data = [
    {"name": "Editha Mnyika", "scores": {"Math": 78, "English": 65, "Physics": 82}},
    {"name": "Godfrey Lyimo", "scores": {"Math": 45, "English": 50, "Physics": 38}},
    {"name": "Consolata Massawe", "scores": {"Math": 90, "English": 88, "Physics": 95}},
    {"name": "Peter Shayo", "scores": {"Math": 40, "English": 35, "Physics": 42}},
]
```
Turn this raw data into a list of `Student` **objects** (not dicts) — you'll need a loop or list comprehension to create one `Student` per entry.

**3. Three list comprehensions** (each must be a genuine one-line list comprehension, not a `for` loop with `.append()`):

- `passing_names` — list of names (strings) of students where `is_passing()` is `True`
- `failing_names` — list of names (strings) of students where `is_passing()` is `False`
- `all_averages` — list of each student's average, **rounded to 1 decimal place**, in the same order as the original list

### Expected output
```python
print(passing_names)
print(failing_names)
print(all_averages)
```
```
['Editha Mnyika', 'Consolata Massawe']
['Godfrey Lyimo', 'Peter Shayo']
[75.0, 44.3, 91.0, 39.0]
```

### Rules
- `average()` must use a loop with a running tracker over `subject_scores.values()` — not `sum()`
- The three final results **must** be list comprehensions — no `.append()` loops for these three
- Use `round(value, 1)` for `all_averages`

Give it a try — take your time, this combines everything from Module 1.
