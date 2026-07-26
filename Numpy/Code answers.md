### Scenario 10

```
import numpy as np

scores = np.array([
    [78, 65, 82],   # Editha
    [45, 50, 38],   # Godfrey
    [90, 88, 95],   # Consolata
    [40, 35, 42],   # Peter
])

print(f"Shape: {scores.shape}")
print(f"Dtype: {scores.dtype}")

godfrey_scores = scores[1]
exam2_scores = scores[:, 1]
consolata_exam3 = scores[2, 2]

print(f"Godfrey's scores: {godfrey_scores}\nExam 2 scores: {exam2_scores}\nConsolata's Exam 3 score: {consolata_exam3}")

```

### Scenario 11

```
import numpy as np

daily_sales_tzs = np.array([150000, 320000, 89000, 410000, 265000])

sales_with_tax = daily_sales_tzs * 1.18
sales_usd = np.round(daily_sales_tzs / 2600, 2)
discounted_sales = daily_sales_tzs - 5000
high_sales_days = daily_sales_tzs > 200000

print(f"Sales with Tax: {sales_with_tax}")
print(f"Sales in USD: {sales_usd}")
print(f"Discounted Sales: {discounted_sales}")
print(f"High Sales Days: {high_sales_days}")

```
