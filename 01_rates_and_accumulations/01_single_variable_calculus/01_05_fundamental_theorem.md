---
title: "fundamental theorem"
part: "part 1 – rates & accumulations"
chapter: "chapter 1 – single-variable calculus"
section: "sec 1.5 – fundamental theorem"
path: "01_rates_and_accumulations/01_single_variable_calculus/01_05_fundamental_theorem.md"
dataset: "covid_daily_cases.csv"
tags: ["📈", "dataset:covid", "level:starter"]
---

## Mini-Hook

"How many infections happened during the first wave?" Suppose we have daily COVID case counts from March through October 2020 in `/datasets/covid_daily_cases.csv`:

```
date,new_cases
2020-03-01,10
2020-03-02,12
...
```

Summing all those daily numbers gives total infections, but that's tedious and noisy. If we fit a smooth logistic curve $c(t)$ to the daily counts, can we get the total with one slick calculation?

## Intuition

Think of $c(t)$ as the cumulative number of cases. Its derivative $c'(t)$ gives daily new cases. Visually, $c(t)$ is that familiar S-shaped logistic climb, while $c'(t)$ is the bell-shaped daily spike. The area under $c'(t)$ between two dates is the change in $c(t)$—literally how many new infections accumulated. So integration and differentiation are two sides of the same story.

## Formal Core

**Fundamental Theorem of Calculus (part I).** If $F$ is any antiderivative of $f$ on $[a,b]$ (so $F'(x)=f(x)$), then
$$\int_a^b f(x)\,dx = F(b)-F(a).$$
*Why care?* It converts messy area computations into simple evaluations of antiderivatives.

**Fundamental Theorem of Calculus (part II).** If $f$ is continuous on $[a,b]$, then the function
$$F(x)=\int_a^x f(t)\,dt$$
 is differentiable and $F'(x)=f(x)$. 
*Why care?* Any cumulative quantity built by integration has the original rate as its derivative.

These twin results guarantee that integration and differentiation undo each other.

## Worked Problems

**🌱 Starter.** Let $f(t)=3t^2$. Find $\int_0^2 f'(t)\,dt$ and explain why it equals $f(2)-f(0)$.

*Solution.* $f'(t)=6t$. Thus
$$\int_0^2 6t\,dt=3t^2\big|_0^2=12.$$
Since $f(2)-f(0)=12-0=12$, the integral matches the net change.

**🌳 Intermediate.** Suppose a logistic model predicts cumulative cases $c(t)=\frac{k}{1+e^{-r(t-20)}}$ with $k=10^5$ and $r=0.25$, where $t$ is days since March 1. Compute the total new cases between day 30 and day 60 using the theorem.

*Solution.* The derivative is
$$c'(t)=\frac{kr e^{-r(t-20)}}{(1+e^{-r(t-20)})^2}.$$
By the theorem,
$$\int_{30}^{60} c'(t)\,dt=c(60)-c(30).$$
Evaluate the logistic function at those times (about $90\%$ of $k$ minus $60\%$ of $k$) to get roughly $30,000$ new cases in that window.

## Level-Up Recap

Instead of summing 210 daily counts, we evaluated the fitted formula at two endpoints. That’s the power of the fundamental theorem.

## Meta-Reflection

The fundamental theorem ties together derivatives and integrals—key themes of 📈 calculus. We’ll soon rely on it for numerical differentiation and later in multivariable settings. Its spirit echoes across linear algebra ⚙️ when we look at adjoint operations, and even in probability 🌀 when accumulation relates to distribution functions.
