# Scenario 04 — Bank Data Quality Checker
**Setting:** You're working with the data team at CRDB Bank in Dar es Salaam. Before any customer record gets loaded into the main system, it needs to pass a basic quality check — missing fields, invalid balances, and bad account numbers cause serious problems downstream.

### The raw inputs
```python
customer = {
    "name": "Fatuma Ally",
    "account_number": "0123456789",
    "balance": 250000,
    "email": "fatuma.ally@crdbmail.co.tz"
}
```

### What you must build — 2 functions

**1. `check_account_number(account_number)`**
- Input: a string
- Returns `True` if the account number is exactly **10 digits long** and contains **only digits**
- Returns `False` otherwise
- Must **return** the boolean — not print it

**2. `check_customer_record(customer)`**
- Input: the `customer` dictionary
- Checks that:
  - `"name"` is not empty
  - `"balance"` is a positive number (greater than 0)
  - `check_account_number()` returns `True` for the account number
- Returns a dictionary in this exact shape:
  ```python
  {"valid": True, "issues": []}
  ```
  or, if something fails:
  ```python
  {"valid": False, "issues": ["list of specific problems found"]}
  ```

### Expected output
```python
result = check_customer_record(customer)
print(result)
```
```
{'valid': True, 'issues': []}
```

### Rules
- `check_account_number` must **return**, not print
- `check_customer_record` must call `check_account_number` internally — don't re-write the digit-check logic inline
- `issues` must be a list, even if empty
- Each function does exactly one job — don't combine the checks into one giant function

Give it a shot — send your code over.
