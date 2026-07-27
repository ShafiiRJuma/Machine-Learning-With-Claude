# Module 3 — Pandas

This is the big one — Pandas is the tool you'll use in almost every real Data Science task: loading, exploring, cleaning, and analyzing datasets. Everything from NumPy (arrays, vectorization, boolean indexing) directly carries over, just wrapped in a friendlier interface with labeled rows and columns.

### What it is
A **DataFrame** is a table — rows and columns, like an Excel sheet, but built for fast programmatic operations. A **Series** is a single column (or row) of a DataFrame — essentially a labeled NumPy array.

### Why it matters for Data Science
Nearly every real dataset you'll ever touch — sales records, survey responses, sensor logs — starts life as a CSV file loaded into a DataFrame. This is the actual day-to-day tool of the job.

### How it works — minimal example
```python
import pandas as pd

df = pd.read_csv("data.csv")
print(df.head())     # first 5 rows
print(df.info())     # column names, types, missing value counts
print(df.shape)       # (rows, columns)
print(df.columns)     # list of column names
```

### The mistake everyone makes
Confusing `.head()` (returns a DataFrame — needs to be printed or it just returns silently in a script) with just typing `df.head` (missing the parentheses — refers to the method itself, not its result — same trap as `f.readlines` back in Scenario 06).

---

# Scenario 15 — Student CSV Loader
**Setting:** The UDSM registrar's office has finally digitized student records into a CSV file. You're building the first script in a pipeline — just loading the data and doing an initial inspection, the same first step every real DS project starts with.

### Step 1 — Create the CSV file yourself
Create a file called `students.csv` with this exact content:
```
name,age,department,gpa
Editha Mnyika,21,Computer Science,3.6
Godfrey Lyimo,23,Economics,2.1
Consolata Massawe,20,Computer Science,3.9
Peter Shayo,22,Business,1.8
Halima Said,21,Computer Science,3.2
```

### What you must build
Plain script:

1. Load the CSV into a DataFrame called `df` using `pd.read_csv()`
2. Print `df.shape`
3. Print `df.columns` (just the column names)
4. Print the first 3 rows using `.head(3)`
5. Print summary info using `.info()`
6. Create `cs_students` — a filtered DataFrame containing only students in the `"Computer Science"` department (boolean indexing, same pattern as NumPy — `df[df['column'] == value]`)
7. Print `cs_students`

### Rules
- Use `pd.read_csv()` — don't manually parse the file with `open()`
- Use `.head(3)`, not manual slicing, to get the first 3 rows
- Filtering must use boolean indexing on the DataFrame, same style as NumPy Scenario 12

Give it a try — send your code when ready.
