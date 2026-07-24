
# Bonus Scenario — M-Pesa Transaction Log Reader
**Setting:** You're helping a small shop owner in Dar es Salaam who exports their M-Pesa transaction history to a text file every week. The export is often messy — some lines get corrupted during export, and some transaction amounts come through as garbage text.

### The raw inputs
Create a text file called `mpesa_log.txt` with this exact content:
```
TXN001|Amina Rashid|15000|received
TXN002|Baraka Mushi|8000|sent
CORRUPTED ROW skip this one
TXN004|Zainab Juma|unknown|received
TXN005|Hassan Ali|22000|sent
TXN006|Halima Said|5000|received
||||
```

### What you must build — 3 functions

**1. `load_transactions(filepath)`**
- Opens the file using a **context manager**
- Returns a list of lines, each stripped of trailing whitespace
- Must handle a missing file with **try/except** — if missing, print `"Transaction file not found."` and return an empty list

**2. `parse_transaction(line)`**
- Splits the line on `|` (no spaces this time — look at the raw format carefully!)
- Expects exactly 4 parts: `txn_id`, `name`, `amount`, `direction`
- Converts `amount` to an `int`
- On success, returns:
  ```python
  {"txn_id": "TXN001", "name": "Amina Rashid", "amount": 15000, "direction": "received"}
  ```
- On **any** failure (wrong number of parts, amount not a number, empty name, etc.) — catch it and return `None`
- Must use try/except, not manual structure checks

**3. `analyze_transactions(filepath)`**
- Loads and parses all lines
- Prints a summary in this exact style:
  ```
  Valid Transactions: 4
  Corrupted Rows: 3
  Total Received: 42000 TZS
  Total Sent: 30000 TZS
  ```
  (`Total Received` = sum of `amount` for valid entries where `direction == "received"`, calculated with a **loop + running tracker**, not `sum()`. Same for `Total Sent`.)

### Rules
- Same try/except requirements as before
- This time, notice the **last row** `||||` — think carefully about what `"||||".split('|')` actually gives you, and why it should fail
- `Total Received` and `Total Sent` must each use a loop with a running tracker — no `sum()`

Give it a try — this time, try writing the full solution yourself first before asking for guided help, since you've already built this pattern once.
