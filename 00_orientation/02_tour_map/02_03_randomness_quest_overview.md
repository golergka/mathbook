---
title: "randomness quest"
part: "part 0 – orientation"
chapter: "chapter 0.2 – tour map"
section: "sec 0.2.3 – randomness quest overview"
path: "00_orientation/02_tour_map/02_03_randomness_quest_overview.md"
dataset: "gps_10s.csv"
tags: ["🌀", "dataset:gps", "level:starter"]
---

## Mini-Hook

The other day my fitness tracker decided I'd teleported across town. One moment it thought I was jogging through the park, the next my location jumped to a coffee shop blocks away. A peek at `datasets/gps_10s.csv` shows the culprit: position readings wiggle from true path $x(t)$ to noisy reports $z(t)$ almost every second.

```
t,x,z
0,0,0.1
1,1,0.9
... (snip) ...
9,9,9.1
```

Random glitches like this make our gadgets seem haunted—and they’re exactly why we need a solid grip on probability.

## Intuition

Noise isn’t just a nuisance—it’s a hint that reality has unpredictable twists. Whether it’s GPS jitter or timing variations in network packets, real systems overflow with randomness. We tame that chaos with probability models: bell curves, Bernoulli trials, or even wilder distributions for extreme events. Thinking in terms of likelihoods lets us handle messy data without panicking whenever a reading looks off.

## Formal Core

1. **Random Variable** – a function assigning a real value to each outcome in a sample space. Why care? Because it turns unpredictable events into measurable quantities.
2. **Expectation $\mathbb{E}[X]$** – the long-run average value of a random variable. Useful whenever single observations bounce around but we want a stable central trend.
3. **Variance $\operatorname{Var}(X)$** – measures typical squared deviation from the mean. High variance warns us that stray points may wander far from expectation.

These basics underpin everything from Kalman filters for smoothing GPS data to algorithms that estimate risk or error rates.

## Worked Problems

### 🌱 Problem
Given the sample below from our GPS log, estimate the average absolute error $|x - z|$ over the 10 seconds.

| t | x | z |
|---|---|---|
| 0 | 0 | 0.1 |
| 1 | 1 | 0.9 |
| 2 | 2 | 2.1 |
| 3 | 3 | 3.0 |
| 4 | 4 | 3.8 |
| 5 | 5 | 5.2 |
| 6 | 6 | 5.9 |
| 7 | 7 | 7.1 |
| 8 | 8 | 8.2 |
| 9 | 9 | 9.1 |

**Solution**
1. Compute each absolute difference $|x - z|$.
2. Sum all ten differences.
3. Divide by 10 to get the average. Here that yields about $0.15$ meters.

### 🌳 Problem
Suppose the noise $n(t) = z(t) - x(t)$ is modeled as Gaussian with mean $0$. Estimate its standard deviation $\sigma$ from the same data.

**Solution**
1. List the ten differences $n(t)$.
2. Square each difference and sum them.
3. Divide by 10 to get the variance $\sigma^2$.
4. Take the square root to find $\sigma \approx 0.18$ meters.

## Meta-Reflection

Randomness pops up all over this book—from smoothing noisy GPS traces (📈 calculus) to analyzing tweet cascades (🌀 probability) and measuring information content (🔧 numerical methods). Later chapters build these ideas into a full toolbox for taming uncertainty.

**This book will fix…**
- maps that jump around when signal quality dips.
- confusion about what “random” really means in data.
- the fear of wobbly measurements ruining conclusions.
