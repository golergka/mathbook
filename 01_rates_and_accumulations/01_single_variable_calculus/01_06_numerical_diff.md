---
title: "numerical diff"
part: "part 1 – rates & accumulations"
chapter: "chapter 1 – single-variable calculus"
section: "sec 1.6 – numerical diff"
path: "01_rates_and_accumulations/01_single_variable_calculus/01_06_numerical_diff.md"
dataset: "covid_daily_cases.csv"
tags: ["📈", "dataset:covid", "level:intermediate", "pattern:ladder"]
---

## Mini-Hook

Ever tried to estimate how fast a pandemic is spreading when you only have day-by-day infection counts? It's like judging the speed of a car by only peeking every 24 hours. Let's see how short numerical bursts can help us approximate that speed and smooth out the noise in real-world data.

## Intuition

Before diving into formulas, picture our daily COVID case counts as dots on a curve. The slope between any two dots hints at how fast cases are rising or falling. But real data is messy—weekends, reporting delays, and sudden spikes all jitter the curve. Numerical differentiation is a way to estimate slopes when perfect, smooth functions aren't handy. Think of it as drawing tiny secant lines between close-by points to approximate the true tangent.

Our Starter scenario uses raw daily counts: we'll compute simple differences to get a crude slope. The Level-Up version refines this by fitting a logistic curve and using centered differences, giving a smoother estimate of the rate of infection growth.

## Formal Core

**Definition 1.6.1 (Forward Difference).** For a discrete sequence $f_0,f_1,\ldots,f_n$ sampled at uniform intervals of width $h$, the *forward difference* at point $i$ is
$$\Delta f_i = \frac{f_{i+1}-f_i}{h}.$$
*Why care?* It provides a first, quick estimate of the derivative using the next data point.

**Definition 1.6.2 (Centered Difference).** A more accurate estimate uses both neighbors:
$$\delta f_i = \frac{f_{i+1}-f_{i-1}}{2h}.$$
*Why care?* Centered differences cancel some of the noise and give second-order accuracy.

**Theorem 1.6.3 (Error Bound).** If $f$ has a continuous third derivative on $[a,b]$, the error in a centered difference approximation satisfies
$$|f'(x_i)-\delta f_i| \le \frac{h^2}{6}\max_{x\in[a,b]}|f'''(x)|.$$
*Why care?* Knowing how the error scales with $h$ helps choose a good step size when balancing accuracy and noise.

## Worked Problems

### 🌱 Starter – Raw Differences
Using `/datasets/covid_daily_cases.csv`, suppose we have daily case counts `c(t)` for March 1–10, 2020:

```
Date,Cases
2020-03-01,35
2020-03-02,43
2020-03-03,55
2020-03-04,70
2020-03-05,98
2020-03-06,150
2020-03-07,210
2020-03-08,250
2020-03-09,300
2020-03-10,370
```

1. Compute the forward differences with $h=1$ day.
2. Identify the day with the fastest increase.

**Solution.**
1. Differences:
   - March 2: $(43-35)/1 = 8$ cases/day
   - March 3: $(55-43)/1 = 12$ cases/day
   - March 4: $(70-55)/1 = 15$ cases/day
   - March 5: $(98-70)/1 = 28$ cases/day
   - March 6: $(150-98)/1 = 52$ cases/day
   - March 7: $(210-150)/1 = 60$ cases/day
   - March 8: $(250-210)/1 = 40$ cases/day
   - March 9: $(300-250)/1 = 50$ cases/day
   - March 10: $(370-300)/1 = 70$ cases/day
2. The biggest jump is on March 10 with an estimated rate of 70 cases/day.

### 🌳 Intermediate – Centered Logistic Fit
Now fit a logistic model $c(t)=\frac{k}{1+Ae^{-rt}}$ with $r=0.25$, $k=100000$, and choose points spaced two days apart for better smoothing. With the same data window, compute the centered difference around March 5.

**Solution.**
1. Evaluate the fitted curve at March 3, 5, and 7:
   - $c(3)\approx\frac{100000}{1+Ae^{-0.75}}$
   - $c(5)\approx\frac{100000}{1+Ae^{-1.25}}$
   - $c(7)\approx\frac{100000}{1+Ae^{-1.75}}$
   For brevity, assume these give $c(3)=1000$, $c(5)=1500$, $c(7)=2300$ cases (illustrative numbers).
2. Using $h=2$ days,
$$\delta c(5) = \frac{2300-1000}{4} = 325\text{ cases/day}.$$
3. This rate is smoother than the raw difference around March 5 and better reflects the logistic trend rather than daily noise.

## Meta-Reflection

Numerical differentiation bridges the gap between pure calculus and real data. We've turned scattered daily counts into a sense of *velocity*—how fast cases grow—without diving into exact formulas. In the next chapter on multivariable calculus 📈, these ideas extend to gradients that guide a drone through blustery winds. If the raw differences here felt jittery, keep an eye out for upcoming chapters on numerical methods 🔧 where stable algorithms tame even noisier situations.

