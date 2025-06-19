---
title: "logistic-curve hook"
part: "part 1 – rates & accumulations"
chapter: "chapter 1 – single-variable calculus"
section: "sec 1.1 – logistic-curve hook"
path: "01_rates_and_accumulations/01_single_variable_calculus/01_logistic_curve_hook.md"
dataset: "covid_daily_cases.csv"
tags: ["📈", "dataset:covid", "level:starter", "pattern:ladder"]
---

## Mini-Hook

You're advising a small city during the early stages of the COVID-19 outbreak. Each day brings more new cases, and everyone wants to know **how bad will it get?** The daily case counts from `datasets/covid_daily_cases.csv` start like this:

```
Date,Daily Cases
2020-03-01,10
2020-03-02,12
2020-03-03,15
2020-03-04,20
2020-03-05,25
```

Just plotting these numbers shows an alarming upward curve. Yet seasoned epidemiologists hint that such surges often level off. How can we tell where things are heading?

## Intuition

Think of an outbreak as a fire. At first it spreads quickly, feeding on plenty of uninfected people—the "fuel." Over time, however, that fuel runs low or countermeasures kick in, and the growth slows. The logistic model captures this S-shaped growth: slow start, rapid rise, gentle plateau. Visualize stacking building blocks where the first few layers take time but eventually fill the box.

## Formal Core

The logistic model assumes the daily case count $c(t)$ evolves according to
\[
\frac{dc}{dt} = r\,c\left(1 - \frac{c}{K}\right),
\]
where $r$ is the intrinsic growth rate and $K$ is the carrying capacity. Solving this differential equation yields
\[
 c(t) = \frac{K}{1 + A e^{-r t}}, \quad\text{with}\quad A = \frac{K - c_0}{c_0}.
\]
This compact formula lets us estimate when the outbreak might peak and how many total cases to expect. **Why care?** Because realistic projections help health officials allocate resources and plan interventions.

## Worked Problems

### 🌱 Starter – Plotting and Predicting
1. **Plot the raw data.** Use the five data points above and extend with a few more days from the dataset. Plot $t$ (days) versus $c(t)$.
2. **Fit a logistic curve.** Choose $r=0.25$ and $K=100000$. Estimate $A$ using the first data point $c_0=10$.
3. **Predict the peak.** Solve for $t$ when $c(t) = K/2$. With the parameters above, the peak occurs around $t \approx (\ln A)/r$ days after March 1.

### 🌳 Intermediate – Parameter Tweaks
1. **Adjust growth rate.** Suppose a new policy slows the spread so $r$ drops to $0.2$. Recompute the peak time.
2. **Estimate total infections.** Integrate $c(t)$ over the outbreak duration. Show that the total approaches $K$ as $t\to\infty$.

Both exercises highlight how the logistic formula turns a messy data table into actionable predictions.

## Meta-Reflection

This first encounter with logistic growth shows how real data can motivate differential equations—a theme we'll revisit soon when we tackle limits and derivatives 📈. Later chapters connect these ideas to other topics like linear algebra ⚙️ (for numerical fitting) and probability 🌀 (for uncertainty). Fun fact: early pandemic models often relied on exactly this logistic approach before moving to more elaborate schemes.
