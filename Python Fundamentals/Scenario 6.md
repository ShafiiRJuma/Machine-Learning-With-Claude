# Scenario 06 — Server Log Analyzer
**Setting:** You're working with the IT team at an internet café chain in Dar es Salaam. Their server writes a log file every time a device connects, but the log file is messy — some lines are malformed. You need to build a script that reads the file, safely parses each line, and reports what's valid vs broken.

### The raw inputs
First, create a text file called `server_log.txt` with this exact content (one entry per line):
```
2024-01-15 08:23:11 | device_id=101 | status=connected
2024-01-15 08:24:02 | device_id=102 | status=disconnected
BAD LINE - no proper structure here
2024-01-15 08:25:47 | device_id=103 | status=connected
2024-01-15 08:26:19 | device_id=abc | status=connected
2024-01-15 08:27:03 | device_id=105 | status=error
```
(Note: line 5 has `device_id=abc` — not a number — which should count as broken too.)

### What you must build — 3 functions

**1. `load_log(filepath)`**
- Opens the file using a **context manager** (`with open(...) as f:`)
- Returns a list of lines (each stripped of trailing whitespace/newlines)
- Must handle the case where the file doesn't exist using **try/except** — if missing, print `"Log file not found."` and return an empty list

**2. `parse_line(line)`**
- Input: one raw line (string)
- Must **try** to split the line into its 3 parts (timestamp, device_id, status) and convert `device_id` to an `int`
- If parsing succeeds, return a dictionary:
  ```python
  {"timestamp": "2024-01-15 08:23:11", "device_id": 101, "status": "connected"}
  ```
- If parsing fails for **any reason** (wrong structure, `device_id` not a number, etc.), catch the error with **except** and return `None`
- This function must use **try/except** — not manual string-structure checks (like counting `|` characters)

**3. `analyze_log(filepath)`**
- Calls `load_log()` to get all lines
- Calls `parse_line()` on each line
- Separates results into two lists: `valid_entries` (successfully parsed dicts) and `broken_count` (a running count of lines that returned `None`)
- Prints a summary in this exact style:
  ```
  Valid Entries: 4
  Broken Lines: 2
  Connected Devices: 2
  ```
  (`Connected Devices` = count of valid entries where `status == "connected"`)

### Rules
- `load_log` and `parse_line` must each use `try/except` — no `if` checks for structure validation
- `parse_line` must not crash the program on bad input — always returns either a dict or `None`
- Must use a context manager (`with`) for file opening

Take your time on this one — it combines three new concepts. Send your code when ready, or ask questions if you want to talk through the approach first.
