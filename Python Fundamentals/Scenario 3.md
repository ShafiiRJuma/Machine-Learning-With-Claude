# Scenario 03 — Dala Dala Fare Tracker
**Setting:** You're helping a dala dala (minibus) conductor in Dar es Salaam track fares collected on a single route run. Passengers pay different amounts depending on distance, and at the end of the trip the conductor wants a quick summary.

### The raw inputs
```python
fares = [400, 400, 600, 400, 1000, 400, 600, 400]
```

### What you must build
Write plain Python (no functions yet) that:
1. Loops through the `fares` list and calculates the **total** collected
2. Finds the **highest** single fare paid
3. Finds the **number of passengers** who paid the highest fare (1000 TZS in this case)
4. Prints a summary using an f-string in this exact style:

```
Total Collected: 4200 TZS
Highest Fare: 1000 TZS
Passengers at Highest Fare: 1
```

### Rules
- You must calculate the total using a **`for` loop with a running tracker variable** — not `sum(fares)`
- You must find the highest fare using `max(fares)` — that one's fine to use directly
- You must count how many passengers paid the highest fare using a **loop with a counter**, not `.count()`
- Must use an f-string for final output

Give it your best shot.
