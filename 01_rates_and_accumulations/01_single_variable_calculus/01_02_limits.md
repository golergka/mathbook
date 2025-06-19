---
title: "limits"
part: "part 1 – rates & accumulations"
chapter: "chapter 1 – single-variable calculus"
section: "sec 1.2 – limits"
path: "01_rates_and_accumulations/01_single_variable_calculus/01_02_limits.md"
dataset: "covid_daily_cases.csv"
tags: ["📈", "dataset:covid", "level:starter"]
---

## Mini-Hook

Imagine plotting the daily COVID-19 cases from `datasets/covid_daily_cases.csv`. At first it looks jumpy—numbers spike and dip day by day. What happens if we zoom in on a particular day and try to estimate the instantaneous growth rate? Without a solid notion of *limits*, those day-to-day jumps remain mysterious.

## Intuition

Think of approaching a destination on a road trip. Even if you only ever check mile markers at whole numbers, you can still get a sense of where you’re headed. Limits formalize that “getting closer” idea. With our case counts, taking smaller and smaller time steps (say half-days or hours) would help us guess how fast the cases are rising at a given moment.

## Formal Core

A function $f(x)$ has a limit $L$ as $x$ approaches $a$ if, for every tolerance $\epsilon > 0$, there exists a proximity $\delta > 0$ such that whenever $0 < |x-a| < \delta$, we have $|f(x)-L| < \epsilon$. In short, $f(x)$ gets arbitrarily close to $L$ whenever $x$ is sufficiently close to $a$.

**Why care?** Limits underpin derivatives and integrals. Without them, talking about instantaneous rates or total accumulated cases would be hand-wavy at best.

### Limit Laws (No-Proof Snapshot)
- Sum: $\lim (f+g) = \lim f + \lim g$
- Product: $\lim (fg) = (\lim f)(\lim g)$
- Quotient: as long as $\lim g \neq 0$, $\lim \frac{f}{g} = \frac{\lim f}{\lim g}$

These rules let us tackle complicated expressions piece by piece.

## Worked Problems

### 🌱 Starter Problem
Using the first three entries of `datasets/covid_daily_cases.csv`, estimate the limit of the average daily increase as $\Delta t \to 0$ near March 2.

**Solution.** The counts are 10 on March 1, 15 on March 2, and 20 on March 3. The average increase from March 1 to March 2 is $5$, and from March 2 to March 3 is also $5$. As we shrink the time window, the estimated rate settles near **5 cases per day**. This numerical approach mirrors the idea of $\lim_{\Delta t\to 0} \frac{c(t+\Delta t)-c(t)}{\Delta t}$.

### 🌳 Intermediate Problem
Show that the logistic model $c(t)=\frac{k}{1+Ae^{-rt}}$ has a finite limit as $t\to\infty$.

**Solution.** Rewrite $c(t)=\frac{k}{1+Ae^{-rt}}$. As $t\to\infty$, the exponential term $e^{-rt}\to 0$. Thus $c(t)\to \frac{k}{1+0}=k$. The limiting total number of cases is the carrying capacity $k$. This highlights why logistic fits are popular—they naturally level off.

## Meta-Reflection

Limits bridge raw data and smooth models. Our quick estimate of case growth hints at the derivative concepts in the next sections 📈. The logistic model’s limiting value foreshadows how integrals will help us tally total infections. Coming up: a deeper dive into $\epsilon$–$\delta$ precision and why continuity matters for trustworthy predictions.
