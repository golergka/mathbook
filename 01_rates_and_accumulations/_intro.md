---
title: "part 1 – rates & accumulations"
path: "01_rates_and_accumulations/_intro.md"
dataset: "covid_daily_cases.csv"
tags: ["📈", "dataset:covid"]
---

## Why this part matters

We live in a world awash with changing numbers—from daily infection counts to the charge levels in a drone’s battery. "Rates" tell us how fast those numbers change, while "accumulations" describe the totals they build up over time. By understanding both, we get a powerful lens on growth, decay, and everything in between.

This part uses a real dataset from `/datasets/covid_daily_cases.csv`. Each line has a `date` and a `cases` count for that day between March and October 2020. We’ll learn how to smooth the noisy daily figures, differentiate them to see trends, and finally integrate them to estimate total infections.

## Escalation road map

1. **Raw counts**: We’ll start by plotting the daily numbers as they come.
2. **Derivative smoothing**: Next, we’ll look at how moving averages and logistic models sharpen the picture.
3. **Integrals**: Finally, summing up the smoothed curve reveals the cumulative impact.

Along the way we’ll peek at logistic growth fits ($r=0.25,\ K=10^5$) and see how simple derivatives and integrals capture the story in the data. No prior knowledge of calculus is assumed—each chapter builds from scratch.

Get ready to explore how ideas of change and accumulation apply far beyond pandemics—into physics, finance, and everyday tech.
