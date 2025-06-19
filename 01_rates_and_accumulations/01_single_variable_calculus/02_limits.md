---
title: "limits"
part: "part 1 – rates & accumulations"
chapter: "chapter 1 – single-variable calculus"
section: "sec 1.2 – limits"
path: "01_rates_and_accumulations/01_single_variable_calculus/02_limits.md"
dataset: "covid_daily_cases.csv"
tags: ["📈", "dataset:covid", "level:starter"]
---

## Mini-Hook
You have daily counts of new cases in `datasets/covid_daily_cases.csv` with columns `date` and `cases` from March–Oct 2020. Plotting these raw counts looks noisy and jagged. To predict when infections will level off, you might try taking a derivative of the data. But how do you take a derivative of something that only updates once per day? This leads straight to the core idea of limits.

## Intuition
Imagine zooming in on two consecutive days, say April 1 and April 2. The cases go from 1000 to 1050. If you could shrink that one-day gap to half a day, or a tenth of a day, how would the jump in cases behave? Limits capture this "what happens as the step gets tiny" mindset. Visually, think of a curve approaching a point so closely that you can barely see the gap. Historically, this idea helped settle nagging questions about instantaneous speed and growth.

## Formal Core
A **limit** describes how a function behaves as its input approaches some value. Formally, we say $\lim_{x\to a} f(x) = L$ if, for every $\epsilon>0$, there exists a $\delta>0$ such that whenever $|x-a| < \delta$, it follows that $|f(x)-L| < \epsilon$.

Why care? Because limits let us define derivatives and integrals rigorously. Without them, "instantaneous change" is just hand-waving.

## Worked Problems
**Problem 🌱**  Using the dataset, estimate the limit of the daily new case count as days approach April 15. Smooth the data by averaging the surrounding 7 days. Show how this approximates the value the counts settle toward.

**Solution**  Slice the CSV file near April 15 and compute the 7-day moving average. The numbers approach about 1200 cases per day. This suggests $c(t)$ is leveling near that value at that time.

**Problem 🌳**  Suppose the spread follows a logistic curve $c(t) = \dfrac{k}{1+e^{-r(t-t_0)}}$ with $r=0.25$ and carrying capacity $k=10^5$. Compute $\lim_{t\to\infty} c(t)$ and explain how this limit relates to total infections.

**Solution**  The exponential term in the denominator vanishes as $t\to\infty$, so $c(t)$ tends to $k$. Thus, the limit is $10^5$. This means if the logistic model holds, daily new cases eventually level off at $k$.

## Meta-Reflection
Limits pave the way for derivatives and integrals 📈. Up next we’ll tighten the screws with $\epsilon$-$\delta$ precision, smoothing the raw counts and setting the stage for a full logistic fit.
