# 📊 Statistics for Data Science — A Beginner's Guide

> **About this guide:** These are my personal learning notes, cleaned up and structured to help others. Whether you're prepping for a data science interview or just starting out — this is for you. 🙌

---

## 📌 Table of Contents

1. [Types of Statistics](#1-types-of-statistics)
2. [Measurement Scales](#2-measurement-scales)
3. [Measures of Central Tendency](#3-measures-of-central-tendency)
4. [Measures of Spread / Dispersion](#4-measures-of-spread--dispersion)
5. [Distributions](#5-distributions)
6. [Empirical Rule (68-95-99.7)](#6-empirical-rule-68-95-997)
7. [Skewness & Kurtosis](#7-skewness--kurtosis)
8. [Positional Averages — Percentiles & Quartiles](#8-positional-averages--percentiles--quartiles)
9. [Correlation](#9-correlation)
10. [Sampling Techniques](#10-sampling-techniques)
11. [Central Limit Theorem (CLT)](#11-central-limit-theorem-clt)
12. [Hypothesis Testing](#12-hypothesis-testing)
13. [ANOVA](#13-anova)
14. [Regression Concepts](#14-regression-concepts)
15. [Handling Missing Values](#15-handling-missing-values)
16. [The Pareto Principle](#16-the-pareto-principle)

---

## 1. Types of Statistics

```
Statistics
├── Descriptive   → Summarize & describe data
└── Inferential   → Draw conclusions from samples about populations
```

| Type | What it does | Example |
|------|-------------|---------|
| **Descriptive** | Summarizes the data you have | Mean age of 100 students = 21 |
| **Inferential** | Makes predictions/decisions about a population using a sample | "Based on 500 voters, Party A will win" |

---

## 2. Measurement Scales

Think of these as **levels of detail** in your data:

| Scale | Description | Can do | Example |
|-------|-------------|--------|---------|
| **Nominal** | Categories with no order | Count | Gender, Color, City |
| **Ordinal** | Categories with order, but gaps aren't equal | Count, Rank | Movie ratings (1★–5★), T-shirt size (S/M/L) |
| **Interval** | Ordered, equal gaps, **no true zero** | +, − | Temperature in °C, Year |
| **Ratio** | Ordered, equal gaps, **has true zero** | +, −, ×, ÷ | Height, Weight, Income |

> 💡 **Memory tip:** *"NOIR"* — Nominal, Ordinal, Interval, Ratio (increasing level of information)

---

## 3. Measures of Central Tendency

These tell you **where the center of your data is**.

### Mean (Average)
Sum of all values divided by the count.

```
Mean (x̄) = (x₁ + x₂ + ... + xₙ) / n

Example: [2, 4, 6, 8, 10]
Mean = (2+4+6+8+10) / 5 = 30 / 5 = 6
```

⚠️ **Sensitive to outliers.** One extreme value can pull the mean far from the "typical" value.

### Median
The **middle value** when data is sorted.

```
Example (odd count):  [1, 3, 5, 7, 9]  → Median = 5
Example (even count): [1, 3, 5, 7]     → Median = (3+5)/2 = 4
```

✅ **Robust to outliers** — great for skewed data like income or house prices.

### Mode
The value that appears **most frequently**.

```
Example: [1, 2, 2, 3, 4, 4, 4, 5]  → Mode = 4
```

- A dataset can have **no mode**, **one mode (unimodal)**, or **multiple modes (bimodal/multimodal)**.
- Best used for **categorical data** (e.g., most common shirt size sold).

---

## 4. Measures of Spread / Dispersion

These tell you **how spread out** the data is around the center.

### Range
```
Range = Maximum value − Minimum value

Example: [3, 7, 2, 9, 1]  → Range = 9 − 1 = 8
```
Simple but **affected by extreme values**.

### Variance (σ² for population, s² for sample)
Average of the **squared differences** from the mean.

```
Variance = Σ(xᵢ − x̄)² / n

Example: [2, 4, 6]
Mean = 4
Differences: (2-4)², (4-4)², (6-4)² = 4, 0, 4
Variance = (4+0+4)/3 = 2.67
```

### Standard Deviation (σ or s)
Square root of the variance. **Same unit as original data**, so easier to interpret.

```
Standard Deviation = √Variance = √2.67 ≈ 1.63
```

> 💡 **Intuition:** If SD is small, data points are close to the mean. If SD is large, data is spread out.

```
Low SD:   ●●●●●●●   (clustered around mean)
High SD:  ●    ●    ●    ●    ●   (spread out)
                ↑
               Mean
```

### Population vs Sample Parameters

| | Population | Sample |
|--|-----------|--------|
| Mean | μ (mu) | x̄ (x-bar) |
| Variance | σ² (sigma squared) | s² |
| Standard Deviation | σ (sigma) | s |

---

## 5. Distributions

A distribution shows how values are **spread across possible outcomes**.

### Uniform Distribution
Every outcome has an **equal probability**.

```
🎲 Rolling a fair die: each face (1–6) has probability 1/6
```

### Bernoulli Distribution
A **single trial** with two outcomes: success (1) or failure (0).

```
🪙 Single coin flip: Heads = 1, Tails = 0
P(Heads) = p,  P(Tails) = 1 − p
```

### Binomial Distribution
**Multiple Bernoulli trials** — counts the number of successes in `n` trials.

```
🪙 Flip a coin 10 times. What's the probability of getting exactly 6 heads?
→ This follows a Binomial distribution with n=10, p=0.5
```

### Poisson Distribution
Number of **events in a fixed interval** (time/space) when events occur independently.

```
📞 Average 3 calls per hour at a call center.
   What's the probability of getting exactly 5 calls in an hour?
→ Poisson distribution with λ (lambda) = 3
```

### Exponential Distribution
Time **between** events in a Poisson process.

```
⏱️ If calls come in at a rate of 3/hour,
   how long until the next call? → Exponential distribution
```

### Geometric Distribution
Number of trials needed to get the **first success**.

```
🎯 How many times do you throw a dart until you hit the bullseye?
```

### Normal Distribution (Gaussian)
The famous **bell curve** — symmetric around the mean.

```
        🔔
     ░░░░░░░░░
   ░░░░░░░░░░░░░
  ░░░░░░░░░░░░░░░
─────────────────────
          μ
```

Many natural phenomena follow this: heights, test scores, measurement errors.

---

## 6. Empirical Rule (68-95-99.7)

For a **normal distribution**, data falls within these ranges:

```
                    ←───── 99.7% (3σ) ─────→
                   ←──── 95% (2σ) ────→
                  ←── 68% (1σ) ──→

        ░░░░░░░░░░░░░░░░░░░░░░░░░░░░
      ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░
    ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░
──────┼─────┼──────┼────┼──────┼─────┼────
    -3σ   -2σ    -1σ   μ    +1σ   +2σ   +3σ

  • 68% of data falls within 1 standard deviation of the mean
  • 95% of data falls within 2 standard deviations
  • 99.7% of data falls within 3 standard deviations
```

> 💡 **Example:** IQ scores have mean=100, SD=15.
> - 68% of people have IQ between 85 and 115
> - 95% between 70 and 130

---

## 7. Skewness & Kurtosis

### Skewness — measures **symmetry**

```
Negative skew         Symmetric (Normal)      Positive skew
(Left-skewed)                                 (Right-skewed)

   ░░                      ░░░                       ░░
  ░░░░░                  ░░░░░░░                   ░░░░░
░░░░░░░░░               ░░░░░░░░░               ░░░░░░░░░
────────────           ────────────           ────────────
Mean < Median         Mean = Median           Mean > Median

e.g., exam scores     e.g., heights           e.g., income,
where most scored                             house prices
high
```

### Kurtosis — measures **tail-ness** (how heavy the tails are)

| Type | Description | Example |
|------|-------------|---------|
| **Mesokurtic** | Normal tails (kurtosis = 3) | Normal distribution |
| **Leptokurtic** | Heavy tails, sharp peak (kurtosis > 3) | Stock returns — rare extreme events |
| **Platykurtic** | Light tails, flat peak (kurtosis < 3) | Uniform-like distributions |

---

## 8. Positional Averages — Percentiles & Quartiles

### Percentiles
A percentile tells you what **percentage of data falls below** a value.

```
Example: Scoring in the 90th percentile on a test means
you scored higher than 90% of test-takers.
```

### Quartiles
Split data into **4 equal parts**:

```
     Q1          Q2 (Median)       Q3
      |                |            |
──────┼────────────────┼────────────┼──────
 25% of data     50% of data   75% of data
```

- **Q1 (25th percentile):** 25% of data is below this
- **Q2 (50th percentile):** The median
- **Q3 (75th percentile):** 75% of data is below this
- **IQR (Interquartile Range) = Q3 − Q1** — the middle 50% spread; used to detect outliers

---

## 9. Correlation

Correlation measures the **strength and direction** of the relationship between two variables.

```
r = +1   Perfect positive correlation  📈
r = 0    No correlation                ➡️
r = −1   Perfect negative correlation  📉
```

### Visual intuition:

```
Positive (r ≈ 0.9)    No correlation (r ≈ 0)    Negative (r ≈ -0.9)
    ●                      ● ●  ●                    ●
   ● ●                   ●    ●  ●                    ● ●
  ●   ●                ●    ●    ●                      ● ●
 ●     ●              ●  ●    ●                            ● ●
────────────          ────────────                    ────────────
Height vs Weight      Shoe size vs IQ             Study hours vs Errors
```

### Types of Correlation Coefficients

| Method | When to use |
|--------|-------------|
| **Pearson's r** | Both variables are continuous, data is normally distributed |
| **Spearman's Rank** | Ordinal data or non-normal distributions — uses ranks instead of raw values |

> ⚠️ **Correlation ≠ Causation!**
> Ice cream sales and drowning rates are positively correlated — but ice cream doesn't cause drowning. Both are caused by hot weather (a confounding variable).

---

## 10. Sampling Techniques

We rarely collect data from an **entire population** — we take a **sample**.

| Technique | How it works | Example |
|-----------|-------------|---------|
| **Random Sampling** | Every individual has equal chance of selection | Drawing names from a hat |
| **Stratified Sampling** | Divide into groups (strata), sample from each | Survey 10% from each age group |
| **Cluster Sampling** | Divide into clusters, randomly pick entire clusters | Select 5 random schools, survey all students |
| **Systematic Sampling** | Pick every kᵗʰ element | Survey every 10th customer |
| **Multi-stage Sampling** | Combination of techniques at multiple stages | Pick states → pick cities → pick households |

---

## 11. Central Limit Theorem (CLT)

> **The most important theorem in statistics.**

**Statement:** As sample size increases (n ≥ 30), the **sampling distribution of the sample mean** approaches a **normal distribution** — *regardless of the shape of the original population.*

```
Population shape:          Sampling distribution of x̄ (n=30+):

  ░░░░                              ░░░
  ░░░░░░░ (skewed)    →           ░░░░░░░   (normal!)
░░░░░░░░░░░                      ░░░░░░░░░
──────────────                   ──────────
  Weird shape                   Bell curve 🔔
```

**Why it matters:**
- Allows us to use normal distribution formulas even when population isn't normal
- Foundation for hypothesis testing and confidence intervals

---

## 12. Hypothesis Testing

A formal way to **test a claim about a population** using sample data.

### The Setup

```
Null Hypothesis (H₀):     "No effect / No change / Status quo"
Alternate Hypothesis (H₁): "There IS an effect / change"
```

**Example:**
```
H₀: New drug has no effect on blood pressure (μ = current level)
H₁: New drug reduces blood pressure (μ < current level)
```

### P-value
The probability of observing your results **if the null hypothesis were true**.

```
p-value < α (significance level, usually 0.05)  → Reject H₀  ✅
p-value ≥ α                                      → Fail to reject H₀  ❌
```

> 💡 A small p-value means your results are unlikely to be due to chance alone.

### Type I and Type II Errors

```
                    Reality
                 H₀ True    H₀ False
Your      Reject H₀ │ Type I ❌  │ Correct ✅  │
Decision  Keep H₀   │ Correct ✅ │ Type II ❌  │
```

| Error | Name | Description | Analogy |
|-------|------|-------------|---------|
| **Type I** | False Positive | Reject H₀ when it's actually true | Convicting an innocent person |
| **Type II** | False Negative | Fail to reject H₀ when it's false | Letting a guilty person go free |

### Degrees of Freedom
The **number of independent values** that can vary in a calculation.

```
Example: If you have 5 numbers that must sum to 20,
once you fix 4 numbers, the 5th is determined.
→ Degrees of freedom = 5 − 1 = 4
```

---

### Types of Tests

#### Parametric Tests
(Assume data follows a known distribution, usually normal)

| Test | When to use |
|------|-------------|
| **t-test** | Small sample (n < 30), population variance unknown |
| **z-test** | Large sample (n ≥ 30), population variance known |

**t-test variations:**
- **One-sample t-test:** Compare sample mean to a known value
- **Two-sample t-test:** Compare means of two groups
- **Paired t-test:** Before/after measurements on the same subjects

#### Non-Parametric Tests
(No assumptions about data distribution — use when data isn't normal)

| Test | When to use |
|------|-------------|
| **Mann-Whitney U** | Compare two independent groups (alternative to 2-sample t-test) |
| **Kruskal-Wallis** | Compare three or more groups (alternative to ANOVA) |

#### Categorical Data Tests

| Test | When to use |
|------|-------------|
| **Chi-Square (χ²)** | Test association between two categorical variables |

```
Example: Is there a relationship between gender and preferred movie genre?
→ Chi-square test
```

---

## 13. ANOVA
**Analysis of Variance** — tests whether the **means of 3 or more groups** are significantly different.

```
Example: Do students from 3 different teaching methods score differently?
Group A (Method 1): mean = 72
Group B (Method 2): mean = 78
Group C (Method 3): mean = 65
→ ANOVA tells you if these differences are statistically significant
```

> If ANOVA is significant → use post-hoc tests (like Tukey's) to see *which* groups differ.

---

## 14. Regression Concepts

### Homoscedasticity vs Heteroscedasticity

These describe the **variance of residuals** (prediction errors) in regression:

```
Homoscedasticity ✅           Heteroscedasticity ❌
(Constant variance)            (Non-constant variance)

   ● ● ●  ●   ●                  ●
── ── ── ── ── ── ──          ── ── ── ── ── ●●●── ──
   ● ●  ●   ● ●                    ● ●● ●●●●●●
```

- **Homoscedasticity:** Variance of errors is consistent across all values of independent variable (desired)
- **Heteroscedasticity:** Variance of errors changes — violates regression assumptions

### Autocorrelation
When **residuals (errors) are correlated with each other** — violates the independence assumption in regression.

```
Example: In time-series data, today's error is correlated with yesterday's error.
→ Detected using the Durbin-Watson test
```

### Multicollinearity
When **two or more independent variables** in a regression model are **highly correlated** with each other.

```
Example: Predicting salary using both "years of experience" and "age"
→ These two are likely highly correlated → multicollinearity problem
```

**Why it's a problem:**
- Makes it hard to isolate the individual effect of each variable
- Inflates standard errors
- Detected using **VIF (Variance Inflation Factor)**

---

## 15. Handling Missing Values

| Method | How | Best for |
|--------|-----|----------|
| **Mean Imputation** | Replace missing with the mean | Normally distributed data, no outliers |
| **Median Imputation** | Replace missing with the median | ⭐ Skewed data or data with outliers |
| **Mode Imputation** | Replace missing with the most frequent value | Categorical data |

> ✅ **Why median imputation is often preferred:**
> The median is not affected by extreme values (outliers). Unlike the mean, it stays close to where most of the data actually is — even when a few values are very large or very small.

```
Example: Income data → [30k, 35k, 40k, 38k, 1M]
Mean  = ~228k  ← Pulled way up by the 1M outlier 😬
Median = 38k   ← Stays near the typical value ✅
```

---

## 16. The Pareto Principle

> **80% of outcomes come from 20% of causes.**

Also called the **80/20 rule**.

```
📊 Examples:
  • 80% of a company's revenue comes from 20% of its customers
  • 80% of bugs in software come from 20% of the code
  • 80% of sales come from 20% of products
```

Useful for prioritization — focus your energy on the 20% that drives the most impact.

---

## 🗂️ Quick Reference Cheat Sheet

```
CENTRAL TENDENCY         DISPERSION
─────────────────        ─────────────────────────
Mean   → Average         Range → Max − Min
Median → Middle value    Variance → Avg squared deviation from mean
Mode   → Most frequent   Std Dev → √Variance

HYPOTHESIS TESTING       ERRORS
─────────────────        ────────────────────────────
H₀: Null (no change)     Type I  → False Positive (α)
H₁: Alternate            Type II → False Negative (β)
p < α → Reject H₀

TESTS
────────────────────────────────────────────────────
Small sample, σ unknown → t-test
Large sample (n≥30), σ known → z-test
3+ group means → ANOVA
Non-normal data, 2 groups → Mann-Whitney U
Non-normal data, 3+ groups → Kruskal-Wallis
Categorical association → Chi-Square

CORRELATION
────────────────────────────────────────────────────
Continuous, normal → Pearson's r
Ordinal / non-normal → Spearman's rank
```


*Made with ❤️ as a learning resource. Feel free to fork, share, and improve!*
