---
title: "Simpson's Paradox: Understanding a Counter-Intuitive Statistical Trap"
date: 2025-12-01
draft: false
description: "Understanding Simpson's Paradox through a simple medical example"
tags: ["data", "statistics", "paradox", "analysis"]
categories: ["Blog"]
---
<img src="feature.png" alt="Simpson's Paradox illustration" style="width: 70%; height: auto; display: block; margin: 0 auto 2rem auto;">


Simpson’s paradox is one of the most puzzling phenomena in statistics. It occurs when a trend observed in several distinct groups **completely reverses** once those groups are combined. In other words, **what appears true within each subgroup can become false when the data is analyzed as a whole**.
<!--more-->

This phenomenon has major implications in medicine, economics, marketing, and the social sciences. Understanding it is essential to avoid incorrect conclusions when analyzing heterogeneous data.

---

# 1. A Simple Medical Example

Imagine a clinical trial involving **160 patients** (80 women and 80 men). These patients receive either a **drug** or a **placebo**. Treatment effectiveness is measured by the recovery rate.

<!-- However, the distribution of treatments is not the same among men and women, which will trigger the paradoxical effect. -->

## Results Among Women

| Women      | Recovered | Not Recovered | Total | Recovery Rate |
|------------|----------:|--------------:|------:|--------------:|
| Drug       | 4         | 16            | 20    | 20%           |
| Placebo    | 18        | 42            | 60    | 30%           |

👉 **Among women, the placebo performs better (30% vs 20%).**

## Results Among Men

| Men        | Recovered | Not Recovered | Total | Recovery Rate |
|------------|----------:|--------------:|------:|--------------:|
| Drug       | 36        | 24            | 60    | 60%           |
| Placebo    | 14        | 6             | 20    | 70%           |

👉 **Among men as well, the placebo is superior (70% vs 60%).**

When analyzing the two groups separately, the conclusion seems clear:  
**the placebo works better.**

## Overall Results

| Overall    | Recovered | Not Recovered | Total | Recovery Rate |
|------------|----------:|--------------:|------:|--------------:|
| Drug       | 40        | 40            | 80    | 50%           |
| Placebo    | 32        | 48            | 80    | 40%           |

👉 **But when the two groups are combined, the drug becomes more effective (50% vs 40%).**

**How can a treatment perform worse in every group, yet better overall?**  
This is exactly what **Simpson’s paradox** reveals.

---

# 2. Why Does the Conclusion Reverse?

The reversal is caused by a **confounding variable** — here, the **sex** of the patients.

In our study:

The drug was mainly given to **men** (who naturally recover more often: 60–70%), while the placebo was mainly given to **women** (who naturally recover less often: 20–30%).

As a result, the drug benefits from a favorable distribution, which **artificially improves its overall performance**.

This composition bias perfectly illustrates the mechanism behind Simpson’s paradox:

> A trend can reverse when the proportions of each group differ.

---

# 3. Real-World Situations Where the Paradox Appears

Simpson’s paradox is not just a theoretical curiosity. It appears regularly in real-world data analyses.

### Medicine
A treatment may seem more or less effective depending on age, sex, or disease stage. Without proper stratification, conclusions can be misleading.

### Marketing Analytics
A lower overall conversion rate may hide better performance across individual channels (mobile, desktop, specific campaigns).

### Human Resources
A department may show strong overall performance while each individual team performs worse when analyzed separately.

### The Berkeley Case (1973)
The university appeared to discriminate against women in admissions. In reality, women applied more often to highly selective departments. Department by department, women were slightly favored.

---

# 4. How to Avoid This Analytical Trap

To protect against incorrect conclusions, several best practices are essential:

## 1. Identify Confounding Variables
Look for factors that influence both the **cause** and the **outcome**.

## 2. Analyze Data by Subgroups
Global statistics are often just a **summary** — and sometimes a misleading one.

## 3. Use Appropriate Statistical Tools
Multivariate regressions, adjusted models, or randomization help avoid the trap.

## 4. Check Group Comparability
Always ask:
- Are the groups comparable?
- Could an unaccounted variable reverse the interpretation?

---

# 5. So Which Analysis Should Be Trusted?

In our example, the answer depends on the question being asked.

### To Measure the Intrinsic Effectiveness of a Treatment:
➡️ Analyze each group separately.  
Here, **the placebo is more effective in every subgroup**.

### To Predict Outcomes in a Population with Similar Composition:
➡️ Look at the aggregated data.  
Here, **the drug performs better overall**.

In clinical trials, the goal is usually to measure the true effectiveness of a treatment. That makes it crucial to control or balance confounding variables.

---

# Conclusion

Simpson’s paradox reminds us that **aggregated data can hide or even reverse real trends**. Meaningful analysis requires understanding the context, identifying structural variables, and choosing the appropriate level of interpretation.

### Key Takeaways

- Global averages can be misleading.  
- Data must be analyzed at the correct scale.  
- Confounding variables must be identified and controlled.  
- A conclusion only makes sense within **its analytical context**.

Before drawing conclusions from aggregated numbers, always ask:

> **“Is there a hidden variable that could explain this trend?”**

This simple precaution can prevent many interpretation errors — even among experienced analysts.
