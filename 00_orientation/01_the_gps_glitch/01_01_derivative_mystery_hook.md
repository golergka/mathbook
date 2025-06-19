---
title: "Derivative Mystery Hook"
part: "part 0 – orientation"
chapter: "chapter 0.1 – the gps glitch"
section: "sec 0.1.1 – derivative mystery hook"
path: "00_orientation/01_the_gps_glitch/01_01_derivative_mystery_hook.md"
dataset: "gps_10s_1hz.csv"
tags: ["📈", "dataset:gps_10s_1hz", "level:starter"]
---

## Mini-Hook: Where Your GPS Goes Haywire

Ever had your running app claim you teleported a few meters in a single second? 
That's a classic consumer-tech fail where GPS noise confuses simple software. 
For our ten-second sample, the location should move smoothly east while nudging north. 
But those jittery readings in `datasets/gps_10s_1hz.csv` tell a different story.
Let's see why finite differences can exaggerate that blip — and how calculus sets it straight.

## Intuition

Picture plotting the coordinates over time. Even a tiny zigzag sends the speed 
calculation spinning. Finite differences just look at "now" and "next" points. 
A single noisy reading is enough to spike the result. The true derivative, in 
contrast, asks how position changes if we zoom infinitely close in time, 
ignoring brief hiccups. It's like smoothing the track in your mind before 
measuring its slope.

## Formal Core

**Definition.** Let $x(t)$ be the true position and $z(t)$ the noisy measurement. 
The finite-difference velocity at time $t$ is
$$v_{\text{FD}}(t) = \frac{z(t+1)-z(t)}{1\ \text{s}}.$$
The true velocity is the limit
$$v(t) = \lim_{\Delta t\to 0} \frac{x(t+\Delta t)-x(t)}{\Delta t}.$$
Why care? Because noisy jumps in $z(t)$ can mislead $v_{\text{FD}}$, while $v(t)$ 
reflects the actual motion.

## Worked Problems

### 🌱 Starter: Spot the Glitch

Using the dataset, compute $v_{\text{FD}}$ between $t=6$ and $t=7$. Explain why 
it doesn't match the trend.

**Solution.** From the CSV, $z(6)=(6,0.6)$ and $z(7)=(7,0.5)$. The finite 
difference gives $(7-6, 0.5-0.6)=(1,-0.1)$, suggesting a slight move south. But 
all other intervals move north or stay level, so this is likely GPS jitter, not a 
real change.

### 🌳 Intermediate: Approaching the True Derivative

Assume the underlying path is $x(t)=(t,0.1t)$ without noise. Show that as 
$\Delta t$ approaches zero, the difference quotient recovers the constant 
velocity $(1,0.1)$ no matter how small $\Delta t$ is chosen.

**Solution.** For $x(t)=(t,0.1t)$,
$$\frac{x(t+\Delta t)-x(t)}{\Delta t}=\frac{(t+\Delta t,0.1(t+\Delta t))-(t,0.1t)}{\Delta t}=(1,0.1).$$
Since this expression does not depend on $\Delta t$, the limit is simply 
$(1,0.1)$, matching the true motion.

## Meta-Reflection

This sneak peek at derivatives shows how calculus smooths out noisy data. 
In the next section we'll hint at using a Kalman filter to tame that noise even 
better. For now, keep in mind that **limits** (📈 calculus) bridge the gap between 
rough finite differences and true motion, a theme we'll revisit throughout the 
book.
