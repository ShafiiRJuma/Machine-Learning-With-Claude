# Scenario 16 — Hospital Records Filter
**Setting:** You're working with a small clinic in Mbeya that keeps patient records in a spreadsheet. The nurse in charge needs to pull specific patients and specific fields quickly — by position, by label, and by condition — without scrolling through the whole sheet manually.

### What it is (quick theory before we build)
- `.loc[]` — selects by **label** (row index label, column name)
- `.iloc[]` — selects by **position** (integer index, like a list) — "i" for integer
- `.query()` — filters using a **string expression**, often more readable than boolean indexing for complex conditions

### Why it matters for Data Science
These three are the daily-driver tools for slicing real datasets — pulling specific rows/columns for a report, extracting a patient cohort, grabbing a single value to double-check something. You'll use all three constantly, often interchangeably depending on what's clearest.

### How it works — minimal example
```python
import pandas as pd

df = pd.DataFrame({
    "name": ["Amina", "Baraka", "Chiku"],
    "age": [30, 45, 22]
})

print(df.loc[0, "name"])        # 'Amina' — row label 0, column 'name'
print(df.iloc[0, 0])            # 'Amina' — row position 0, column position 0
print(df.iloc[1:3])             # rows at position 1 and 2 (Baraka, Chiku)
print(df.query("age > 25"))     # rows where age > 25
```

### The mistake everyone makes
Using `.iloc` with a column **name** (`df.iloc[0, "name"]` — ❌ crashes, `iloc` only accepts positions) or using `.loc` with a column **position** — mixing the two up is the #1 source of confusion here.

---

## The scenario

### Step 1 — Create the CSV file
Create `patients.csv` with this exact content (use the file-writing method from last scenario to avoid line-break issues):
```
patient_id,name,age,condition,temperature
P001,Amina Rashid,34,malaria,39.2
P002,Baraka Mushi,58,hypertension,37.1
P003,Chiku Juma,5,malaria,38.9
P004,Daudi Kessy,67,diabetes,36.8
P005,Editha Mwakisu,29,malaria,40.1
P006,Faraja Ngowi,45,hypertension,38.5
```

### What you must build
Plain script:

1. Load into `df`
2. `first_patient_name` — use `.iloc` to get the `name` value of the **first row** (position-based)
3. `row_by_label` — use `.loc` to get the **entire row** where the index label is `2` (this is Chiku Juma — remember, default index labels match position unless you've changed them)
4. `malaria_patients` — use `.query()` to get all rows where `condition == "malaria"`
5. `high_fever` — use `.query()` to get all rows where `temperature > 38.5`
6. `young_malaria_patients` — use `.query()` with **two combined conditions**: `condition == "malaria"` **and** `age < 18`
7. Print all in this exact style:
```
First Patient: Amina Rashid
Row by Label 2:
patient_id            P003
name            Chiku Juma
age                       5
condition           malaria
temperature            38.9
Name: 2, dtype: object

Malaria Patients: 3
High Fever Patients: 4
Young Malaria Patients: 1
```

### Rules
- Must use `.iloc` for `first_patient_name` (position-based)
- Must use `.loc` for `row_by_label` (label-based)
- Must use `.query()` (string expression) for all three filtered DataFrames — not boolean indexing this time
- For counts in the final prints, use `len()` on the filtered DataFrames

Give it a try — send your code when ready.
