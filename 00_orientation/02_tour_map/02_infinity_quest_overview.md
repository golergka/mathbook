---
title: "Infinity Quest Overview"
part: "part 0 – orientation"
chapter: "chapter 0.2 – tour map"
section: "sec 0.2.2 – infinity quest overview"
path: "00_orientation/02_tour_map/02_infinity_quest_overview.md"
dataset: "gps_10s_1hz.csv"
tags: ["🧩", "dataset:gps", "level:intro"]
---

## Mini-Hook
Your phone's map app once sent you in endless circles when trying to find a coffee shop. The **10‑second GPS log** in `datasets/gps_10s_1hz.csv` shows jitter that confuses the app, making it look like you're walking a crazy loop.

## Intuition
Infinity isn't just about large numbers—it often shows up when a process refuses to settle down. Picture that looping GPS trail: each noisy step adds a bit of extra distance, and in theory you could keep counting steps forever. We'll see how mathematics tames those spirals.

## Formal Core
We'll explore how sequences $(a_n)$ describe an unfolding process and how their sums $S_N=\sum_{n=1}^N a_n$ can approach a limit. If the partial sums get closer and closer to some value $S$, we say the series converges. Otherwise, the total distance can blow up just like our malfunctioning map app.

## Worked Problems
### 🌱 Starter
Using `gps_10s_1hz.csv`, compute the straight-line displacement from start to end:
1. Convert latitude and longitude to meters (approx. 111,000 meters per degree).
2. Subtract the first coordinates from the last to get $\Delta x$ and $\Delta y$.
3. Distance $\approx \sqrt{\Delta x^2+\Delta y^2} \approx 1.2$ meters.

### 🌳 Intermediate
Estimate the path length if you naively connect each GPS dot:
1. Compute differences between successive lat/lon pairs.
2. Convert to meters and sum the segment lengths.
3. Because of jitter, this "polyline" is about 5 meters—much longer than the real displacement, hinting at an infinite zigzag if we kept collecting data.

## Meta-Reflection
This glimpse of runaway path length foreshadows topics like series convergence 📈 and even chaos in dynamical systems. Later chapters will give you the tools to decide when adding up infinitely many jittery steps actually makes sense.

### This book will fix…
- Distinguishing real movement from noisy chatter.
- Revealing how calculus formalizes infinite processes.
- Offering strategies to keep your apps from looping forever.
