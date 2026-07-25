# Scenario 07 — Host Inventory Manager
**Setting:** You're helping the IT team at an internet café chain in Dar es Salaam manage their computer inventory. Each café location has multiple host machines (desktops), and staff need an easy way to track each machine's status and usage without repeating the same logic over and over. This is your first OOP scenario — instead of separate functions and loose dictionaries, you'll wrap related data and behavior together into a **class**.

### What it is (quick theory before we build)
A **class** is a blueprint for creating objects that bundle data (**attributes**) and behavior (**methods**) together. An **object** is one specific instance created from that blueprint.

### Why it matters for Data Science
Later, when you use Pandas, every `DataFrame` you touch is actually an *object* — it has attributes (`.shape`, `.columns`) and methods (`.head()`, `.dropna()`) bundled together. Understanding classes now is what makes Pandas' behavior click instead of feeling like magic.

### How it works — minimal example
```python
class Student:
    def __init__(self, name, gpa):
        self.name = name
        self.gpa = gpa

    def is_honors(self):
        return self.gpa >= 3.5

s1 = Student("Amina", 3.8)
print(s1.name)         # Amina
print(s1.is_honors())  # True
```
- `__init__` runs automatically when you create a new object — it sets up the object's starting attributes
- `self` refers to *this specific object* — it's how a method accesses its own data
- You call a method with `object.method()`, no need to pass `self` yourself — Python does that automatically

### The mistake everyone makes
Forgetting `self` as the first parameter of every method:
```python
def is_honors():          # ❌ missing self — will crash when called as s1.is_honors()
    return self.gpa >= 3.5
```

---

## Now the scenario

### What you must build — 1 class: `Host`

**Attributes** (set in `__init__`):
- `host_id` (string, e.g. `"H01"`)
- `location` (string, e.g. `"Kariakoo Branch"`)
- `status` (string — either `"active"` or `"under_repair"`)
- `hours_used` (starts at `0`, tracks total usage)

**Methods:**
1. `log_usage(hours)` — adds `hours` to `hours_used` (no return, just updates the attribute)
2. `mark_for_repair()` — sets `status` to `"under_repair"`
3. `mark_active()` — sets `status` back to `"active"`
4. `summary()` — **returns** a string in this exact format:
   ```
   H01 (Kariakoo Branch): active, 12 hrs used
   ```

### What to test it with
```python
h1 = Host("H01", "Kariakoo Branch", "active")
h1.log_usage(5)
h1.log_usage(7)
print(h1.summary())

h1.mark_for_repair()
print(h1.summary())
```

### Expected output
```
H01 (Kariakoo Branch): active, 12 hrs used
H01 (Kariakoo Branch): under_repair, 12 hrs used
```

### Rules
- `hours_used` must default to `0` inside `__init__` — don't require it as a parameter
- `log_usage` must **accumulate** (add to existing hours), not overwrite
- `summary()` must **return** the string, not print it directly (printing happens outside, via `print(h1.summary())`)

Give it a try — write the full `Host` class and the test code.
