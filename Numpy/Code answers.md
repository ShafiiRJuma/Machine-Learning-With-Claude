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
