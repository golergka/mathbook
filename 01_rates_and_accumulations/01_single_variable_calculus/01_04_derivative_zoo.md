---
title: "derivative zoo"
part: "part 1 – rates & accumulations"
chapter: "chapter 1 – single-variable calculus"
section: "sec 1.4 – derivative zoo"
path: "01_rates_and_accumulations/01_single_variable_calculus/01_04_derivative_zoo.md"
dataset: "covid_daily_cases.csv"
tags: ["📈", "dataset:covid", "level:starter", "pattern:ladder"]
---

## Mini-Hook

You’ve been tracking daily COVID-19 cases in a spreadsheet.  The raw numbers jitter from one day to the next, but the overall curve climbs and then levels off.  You want to know how quickly the pandemic is spreading *right now*.  Derivatives—the instantaneous rates of change—turn those noisy counts into a clear picture of acceleration or slowdown.

## Intuition

Think of a roller coaster climbing a hill.  At each point, the slope tells you how steep the track is.  In calculus, that slope is the derivative.  For smooth curves, we can often guess what the slope looks like just by imagining how a tiny change in the input affects the output.  A parabola curves more steeply as you move away from the center, while a sine wave oscillates between steep climbs and gentle plateaus.  The logistic model $f(t)=\dfrac{k}{1+e^{-r(t-t_0)}}$ mimics an outbreak that grows quickly and then tapers off.  Its derivative reveals when the spread peaks and how fast it fades.

## Formal Core

Here’s a quick tour of the most common derivative rules:

1. **Power Rule.** If $f(t)=t^n$, then $f'(t)=n t^{n-1}$.  Handy for polynomials.
2. **Product Rule.** For $f(t)=u(t)v(t)$, the derivative is $f'(t)=u'(t)v(t)+u(t)v'(t)$.  This captures how two changing parts interact.
3. **Chain Rule.** When $f(t)=g(h(t))$, you multiply rates: $f'(t)=g'(h(t))h'(t)$.  This is the secret sauce behind the logistic derivative.

**Example.** With $f(t)=\dfrac{k}{1+e^{-r(t-t_0)}}$, let $u(t)=1+e^{-r(t-t_0)}$.  Then $f(t)=k u(t)^{-1}$.  By the chain and power rules,
$$
 f'(t) = k (-1) u(t)^{-2} \cdot u'(t) = \frac{k r e^{-r(t-t_0)}}{\bigl(1+e^{-r(t-t_0)}\bigr)^2}.
$$
This bell-shaped curve pinpoints the outbreak’s fastest growth.

## Worked Problems

**🌱 Starter.** Let $c(t)$ be the daily case count from `datasets/covid_daily_cases.csv`.  Suppose the data around day 50 fits $c(t)=400+20 t-0.2 t^2$.  Find $c'(50)$.

*Solution.*  Using the power rule, $c'(t)=20-0.4 t$.  Evaluating at $t=50$ gives $c'(50)=20-0.4\times50=0$.  The growth rate has momentarily flattened.

**🌳 Intermediate.** The logistic fit uses $r=0.25$ and $k=10^5$.  If the midpoint occurs at $t_0=80$, compute the derivative $f'(t)$ at $t=80$ and interpret it.

*Solution.*  Plugging into the derivative formula above with $t=t_0$,
$$
 f'(t_0)=\frac{k r e^{0}}{\bigl(1+e^{0}\bigr)^2}=\frac{10^5 \times 0.25}{4}=6250.
$$
At day 80 the outbreak is growing fastest at about 6,250 new cases per day.

## Meta-Reflection

Derivatives let us peer beneath the surface of raw data and see momentum.  In the next section we’ll connect these rules back to the grand story of calculus—the Fundamental Theorem—which links those instantaneous rates to overall changes over time 📈.  If you’re itching to explore how numerical methods estimate derivatives when data is messy, hang tight: a dedicated chapter awaits.
