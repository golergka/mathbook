---
title: "Drone Path Hook"
part: "part 1 – rates & accumulations"
chapter: "chapter 2 – multivariable calculus"
section: "sec 2.1 – drone path hook"
path: "01_rates_and_accumulations/02_multivariable_calculus/02_01_drone_path_hook.md"
tags: ["📈", "level:starter"]
---

## Mini-Hook

A hobbyist drone (mass $1\,$kg, battery $50\,$Wh) has to travel from point A to point B with a steady crosswind of $2\,$m/s. If it simply flies straight, the battery might drain before it reaches the destination. How can a smarter path save precious energy?

## Intuition

Imagine a paper airplane gliding across a breeze. The wind nudges it off course, so you tilt your throw to compensate. For a drone, we have motors and sensors to correct the drift. But constant corrections waste battery. Instead, we want a path that naturally rides the wind when possible. By treating the drone’s energy usage like a gentle slope to roll down, we can let calculus guide the way.

## Formal Core

We define an energy cost functional $E[\gamma]$ for a path $\gamma(t)$ with velocity $\dot\gamma(t)$. In still air, energy roughly scales like the square of speed. A wind vector $\mathbf{w}=(2,0,0)\,$m/s modifies the effective velocity to $\dot\gamma(t)-\mathbf{w}$. The goal is to minimize
$$E[\gamma]=\int_0^T \|\dot\gamma(t)-\mathbf{w}\|^2\,dt$$
subject to $\gamma(0)=A$ and $\gamma(T)=B$. Gradient descent on this functional gives a vector field guiding the drone toward an efficient path. The key idea is to treat $E$ as a surface in a high-dimensional space; a small change in $\gamma$ creates a slope along which we can descend to a lower-energy route.

## Worked Problems

### 🌱 Starter: Straight-Line Guess

**Problem.** With no wind, a drone travels $100\,$m in $20\,$s along a straight line. Estimate the energy cost if $E[\gamma]$ reduces to $\int \|\dot\gamma(t)\|^2 dt$ and the drone maintains constant speed.

**Solution.** A straight line means constant speed $v=100/20=5\,$m/s. The integrand $\|\dot\gamma(t)\|^2$ equals $v^2=25$. Over $20\,$s, the cost is $\int_0^{20} 25\,dt=25\times20=500$ (in whatever units our model uses). Even this simple model shows how speed squared dominates energy use.

### 🌳 Intermediate: First Descent Step

**Problem.** Now include a wind $\mathbf{w}=(2,0,0)$. Starting from the straight-line path $\gamma_0(t)$, compute the variation $\delta E$ for a small deviation $\eta(t)$ with $\eta(0)=\eta(T)=0$. Show how the gradient descent update arises.

**Solution.** Write $\gamma=\gamma_0+\epsilon\eta$. Then
$$E[\gamma]=\int_0^T \|\dot\gamma_0+\epsilon\dot\eta-\mathbf{w}\|^2 dt.$$
Expanding and keeping terms up to first order in $\epsilon$ gives
$$E[\gamma]=E[\gamma_0]+2\epsilon\int_0^T (\dot\gamma_0-\mathbf{w})\cdot\dot\eta\,dt +O(\epsilon^2).$$
Integrating by parts and using $\eta(0)=\eta(T)=0$ yields
$$\delta E=2\epsilon\int_0^T -\ddot\gamma_0\cdot\eta\,dt.$$
Thus the functional gradient is $-2\ddot\gamma_0$. A descent step updates the path by moving opposite this gradient, nudging $\gamma$ toward a curve whose acceleration balances the wind.

## Meta-Reflection

This section hints at how multivariable calculus tackles optimization in the wild 📈. We treated a drone path as a curve to tweak, a perspective that returns in gradient/gradient-descent methods. Upcoming sections dive deeper into vector calculus tools for understanding and controlling motion in multiple dimensions. Farther ahead we’ll revisit the drone with more advanced models (think differential equations and control theory). For now, keep an eye on how gradients quietly shape efficient motion.

