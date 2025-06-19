---
title: "Derivative Mystery Hook"
part: "part 0 – orientation"
chapter: "chapter 0.1 – the gps glitch"
section: "sec 0.1.1 – derivative mystery hook"
path: "00_orientation/01_the_gps_glitch/01_derivative_mystery_hook.md"
dataset: "gps_10s_1hz.csv"
tags: ["📈", "dataset:gps", "level:starter"]
---

## Mini-Hook
You fire up a running tracker on your phone, expecting a smooth path. Halfway through your jog, the map shows a sudden sideways leap—your GPS glitched, and now your pace estimate is totally off. **How fast were you really moving?** We'll use a short 10‑second log where $x(t)$ is the true position and $z(t)$ is the noisy measurement:

```
# datasets/gps_10s_1hz.csv (time in seconds)
time,x_true,z_noisy
0,0,0.2
1,1,1.5
...
```

## Intuition
Finite differences let us approximate velocity by comparing consecutive positions. But when $z(t)$ jitters, the computed velocity can jump wildly. Think of measuring distance with a ruler that keeps sliding around—a tiny wobble leads to big errors.

## Formal Core
Given discrete times $t_i$, the naive velocity estimate is
$$v_i=\frac{z(t_{i+1})-z(t_i)}{t_{i+1}-t_i}.$$
If $z(t)$ closely tracks $x(t)$, this works well. With noise, we’re effectively differentiating error terms, which amplifies them. Understanding why requires recognizing that differentiation is a high-pass filter—great for catching sharp changes, awful when your data is shaky.

## Worked Problems
1. 🌱 **Estimate Velocity**  
   Using the raw $z(t)$ values above, compute $v_i$ for $i=0,1,\ldots,8$. Notice how the estimate at $t=3$ spikes because $z(4)$ overshoots.
2. 🌳 **Compare to True**  
   Repeat using $x(t)$ for the numerator. The velocities now march smoothly at roughly $1\,\text{m/s}$. The difference highlights how noise skews finite differences.

## Meta-Reflection
A basic derivative from noisy data can mislead us. Next, we'll see a sneak peek of a tool—the Kalman filter—that smooths out $z(t)$ before taking differences. This sets the stage for more serious analyses later in the book (📈 calculus, 🔧 numerical methods).
