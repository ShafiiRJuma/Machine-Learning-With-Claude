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

### Scenario 12

```
import numpy as np

scores = np.array([
    [78, 65, 82],   # Editha
    [45, 50, 38],   # Godfrey
    [90, 88, 95],   # Consolata
    [40, 35, 42],   # Peter
])

student_averages = np.round(scores.mean(axis=1), 2)
exam_averages = np.round(scores.mean(axis=0), 2)
overall_std = np.round(scores.std(), 2)
highest_exam_avg_index = np.argmax(exam_averages)

print(f"Student Averages: {student_averages}")
print(f"Exam Averages: {exam_averages}")
print(f"Overall Std: {overall_std}")
print(f"Highest Average Exam Index: {highest_exam_avg_index}")

```

### Scenario 13

```
import numpy as np

repayments = np.array([45000, 50000, 2000, 48000, 500000, 47000, 1000, 52000, 49000, 300000])

low_outliers = repayments[repayments < 5000]
high_outliers = repayments[repayments > 200000]
normal_range = repayments[(repayments >= 5000) & (repayments <= 200000)]
outlier_count = len(low_outliers) + len(high_outliers)

print(f"Low Outliers: {low_outliers}")
print(f"High Outliers: {high_outliers}")
print(f"Normal Range: {normal_range}")
print(f"Outlier Count: {outlier_count}")
```

### Scenario 14

```
import numpy as np

students = ["Editha", "Godfrey", "Consolata", "Peter"]
scores = np.array([
    [78, 65, 82],   # Editha: Quiz, Midterm, Final
    [45, 50, 38],   # Godfrey
    [90, 88, 95],   # Consolata
    [40, 35, 42],   # Peter
])
weights = np.array([0.2, 0.3, 0.5])   # Quiz 20%, Midterm 30%, Final 50%

final_grades = np.dot(scores, weights)
final_grades_rounded = np.round(final_grades, 2)
top_student_index = np.argmax(final_grades)
top_student_name = students[top_student_index]
score_vector_norm = np.round(np.linalg.norm(scores[2]), 2)

print(f"Final Grades: {final_grades_rounded}")
print(f"Top Student: {top_student_name} (Grade: {final_grades_rounded[top_student_index]})")
print(f"{top_student_name}'s Score Vector Norm: {score_vector_norm}")

```
