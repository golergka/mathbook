---
title: "Kalman Filter Foreshadow"
part: "part 0 – orientation"
chapter: "chapter 0.1 – the gps glitch"
section: "sec 0.1.2 – kalman filter foreshadow"
path: "00_orientation/01_the_gps_glitch/02_kalman_filter_foreshadow.md"
dataset: "gps_10s_1hz.csv"
tags: ["📈", "dataset:gps", "level:intermediate"]
---

## Mini-Hook
Remember that rogue jump in your running app? What if you could smooth out those glitches automatically? Reusing the same GPS log, we'll sneak a preview of the Kalman filter—an algorithm that cleverly blends predictions and noisy measurements.

## Intuition
Imagine predicting where you'd be next if you kept a steady pace. When the GPS reading $z(t)$ arrives, you nudge that guess rather than trusting the noisy measurement outright. Over time, the filter learns how much to trust your model versus the sensor. It's like averaging your past stride with the shaky phone data.

## Formal Core
A simple Kalman update for position and velocity can be sketched as
$$
\begin{aligned}
\hat{x}_{t+1}^- &= \hat{x}_t + \hat{v}_t \,\Delta t,\\
K_t &= \frac{P_t}{P_t + R},\\
\hat{x}_{t+1} &= \hat{x}_{t+1}^- + K_t \bigl(z_{t+1}-\hat{x}_{t+1}^-\bigr),\\
P_{t+1} &= (1-K_t)P_t + Q.
\end{aligned}
$$
Here $P_t$ represents our uncertainty, $R$ the measurement noise, and $Q$ how uncertain our motion model is. The key idea: by filtering before differentiating, we tame the noise that ruined our finite differences.

## Worked Problems
1. 🌱 **One-Step Update**  
   Starting with $\hat{x}_0=0$ and $\hat{v}_0=1$, compute $\hat{x}_1$ using $z(1)=1.5$ and reasonable guesses for $P_0$, $R$, and $Q$.
2. 🌳 **Smooth the Entire Log**  
   Apply the update repeatedly for all ten seconds and compare the smoothed path to $x(t)$. Notice how the estimated velocities stabilize compared to the raw finite differences from the previous section.

## Meta-Reflection
This quick taste of a Kalman filter shows how modeling and data work together. We'll return to these ideas later when tackling numerical methods and control theory (🔧, part 6). For now, just remember: a bit of math can make those annoying GPS glitches much less painful.
