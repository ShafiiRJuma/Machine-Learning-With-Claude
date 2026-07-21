# Scenario 02 — Airtime Vending Machine
**Setting:** You're building a simple script for a Vodacom/M-Pesa airtime vending kiosk in Dar es Salaam. A customer inserts cash, and the machine must validate the amount and issue airtime accordingly.

### The raw inputs
```python
amount_inserted = 1500
min_amount = 500
max_amount = 50000
```

### What you must build
Write plain Python (no functions yet) that:
1. Checks if `amount_inserted` is within the valid range (`min_amount` to `max_amount`, inclusive on both ends)
2. Uses a **ternary expression** (not a full if/else block) to set a variable called `status_message` to either `"Valid"` or `"Invalid"`
3. Prints the result using an f-string in this exact style:

```
Amount: 1500 TZS
Status: Valid
```

### Rules
- The validity check must use **boolean logic with `and`** — e.g. `min_amount <= amount_inserted <= max_amount` or an equivalent `and` expression
- `status_message` must be assigned using a **ternary expression**, like:
  ```python
  x = "yes" if condition else "no"
  ```
  Not a full `if/else:` block
- Must use an f-string for the final print

Give it a try — send your code over.
