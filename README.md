# Assignment 2 — Genetic Algorithm: Knapsack Problem
## Observation Report

**Student Name  :** KASHIFA
**Student ID    :** 2310049146
**Date Submitted:** 21/3/2026

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `ga_knapsack.py` and read through it. Then answer these questions.

**Q1. What does the `fitness()` function return? Why does an overweight solution score 0?**

```
[The fitness() function returns the total value of selected items if the total weight is within the limit. If the total weight exceeds the maximum capacity, it returns 0. This penalizes invalid solutions so they are not selected.]
```

**Q2. What does `tournament_select()` do? Why are higher-fitness individuals more likely to be chosen?**

```
[tournament_select() randomly selects a few individuals and chooses the one with the highest fitness among them. This increases the probability of selecting better solutions. Hence, individuals with higher fitness are more likely to be chosen.]
```

**Q3. Look at the `run_ga()` loop. Find this line:**
```python
next_gen = [best_chromosome[:]]
```
**What is this doing? Why is it important to always keep the best solution?**

```
[This copies the best chromosome from the current generation into the next generation. It ensures that the best solution is not lost. This is called elitism and helps the algorithm converge faster.]
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python ga_knapsack.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of generations | 50 |
| Best value at generation 1 | 60 |
| Final best value | 77 |
| Total weight of best solution (kg) | 14.4 |
| Is solution valid (Yes / No) | Yes |

**Copy the printed packing list here:**
```
[Water bottle
First aid kit
Sleeping bag
Torch
Energy bars (x6)
Rain jacket
Map & compass
Cooking stove
Rope (10 m)
Sunscreen
Power bank ]

```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest improvement happen? Does the curve flatten at some point?*
```
[ The graph shows a sharp increase in fitness during the first few generations, rising quickly from 60 to around 75. After that, the improvement becomes very slow and the curve flattens near 77. This indicates that the algorithm has converged and is no longer finding significantly better solutions. ]
```

---

## Experiment 2 — Effect of Mutation Rate

**Instructions:** In `ga_knapsack.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `mutation_rate` = **0.01**, **0.05**, and **0.30**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| mutation_rate | Final best value | Weight (kg) | Valid? | Shape of curve |
|--------------|-----------------|-------------|--------|----------------|
| 0.01         | 75              | 14.9        | Yes    | Fast rise then early flattening (stuck) |
| 0.05         | 77              | 14.4        | Yes    | Smooth rise then stable convergence |
| 0.30         | 78              | 14.1        | Yes    | Fluctuating, more exploration, higher peak |



**Compare the three plots. What happens when mutation is too low? Too high? (3–4 sentences)**  
*Hint: Too low = no diversity, may get stuck. Too high = random search. What is the sweet spot?*
```
[When mutation is too low (0.01), the algorithm quickly converges but gets stuck in a local optimum due to lack of diversity. When mutation is too high (0.30), the search becomes more random and less stable, though it may occasionally find better solutions. A moderate mutation rate (0.05) provides a balance between exploration and exploitation, leading to stable convergence. This balance is the sweet spot for effective performance.]
```

**Which mutation_rate gave the best result? Why do you think that is?**
```
[The mutation rate 0.30 gave the highest value (78). This is because higher mutation increases exploration and helps discover better solutions. However, 0.05 is more reliable as it provides consistent and stable results.]
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final value | Main finding in one sentence |
|------------|-------------|-------------|------------------------------|
| 1 — Baseline | mutation_rate = 0.05 | 77 | GA converges quickly and stabilizes after a few generations |
| 2 — Mutation rate | mutation_rate = 0.30 | 78 | Higher mutation improves exploration and can find better solutions but is less stable |

**In your own words — what is the most important thing you learned about Genetic Algorithms from these experiments? (3–5 sentences)**
```
[ The most important thing I learned is that Genetic Algorithms depend heavily on parameter tuning, especially mutation rate. If the mutation rate is too low, the algorithm loses diversity and gets stuck in local optima. If it is too high, the search becomes random and unstable. A balanced mutation rate helps achieve good convergence and better solutions efficiently. ]
```

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, packing list pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
