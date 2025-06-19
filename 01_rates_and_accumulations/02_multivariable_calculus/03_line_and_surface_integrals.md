---
title: "Line & surface integrals"
part: "part 1 – rates & accumulations"
chapter: "chapter 2 – multivariable calculus"
section: "sec 2.3 – line & surface integrals"
path: "01_rates_and_accumulations/02_multivariable_calculus/03_line_and_surface_integrals.md"
dataset: "drone_flight_log.csv"
tags: ["📈", "dataset:drone", "level:starter", "pattern:ladder"]
---

## Mini-Hook
Imagine piloting a small delivery drone on a windy day. You receive a GPS log with positions recorded every second: time $t$, $x$ and $y$ coordinates (in meters), and altitude $z$. The drone must fight a constant headwind of $2\,\text{m/s}$ eastward. How much extra battery power will that wind sap as the drone travels along its recorded path?

*Starter version:* Using basic single-variable calculus, we could estimate the energy cost along the straight-line segments between points.

*Level-Up version:* By treating the path as a continuous curve and accounting for wind as a vector field, line integrals give us a cleaner and more accurate calculation.

## Intuition
Line integrals extend ordinary integration to curved paths. Picture dragging a lightweight sled along a winding track while wind pushes against it. Instead of summing force times tiny straight distances, you integrate the dot product of force and the tangent vector along every point of the path. Surface integrals do a similar job for flows through surfaces—imagine measuring how much wind passes through a large tilted window.

## Formal Core
**Definition (Line Integral).** Given a vector field $\mathbf{F}$ and a parametrized path $\mathbf{r}(t)$, the line integral of $\mathbf{F}$ along $\mathbf{r}$ from $t=a$ to $t=b$ is
$$\int_a^b \mathbf{F}(\mathbf{r}(t)) \cdot \mathbf{r}'(t)\,dt.$$
*Why care?* It measures cumulative work along a path—a staple for physics, engineering, and even graphics.

**Definition (Surface Integral).** For a surface parametrized by $\mathbf{r}(u,v)$ and vector field $\mathbf{F}$, the flux through the surface is
$$\iint_S \mathbf{F} \cdot (\mathbf{r}_u \times \mathbf{r}_v)\,du\,dv.$$
*Why care?* It tells you how much of a vector field passes through a surface—useful for fluid flow or electromagnetic flux.

## Worked Problems
**🌱 Easier:** Suppose the drone travels on a circular path of radius $10\,\text{m}$ at constant speed. The wind is constant $\mathbf{W}=(2,0,0)\,\text{m/s}$. Parametrize the circle with $\mathbf{r}(t)=(10\cos t,10\sin t,0)$ for $0\le t\le 2\pi$. Compute the work done by the wind along one loop.

*Solution:* The tangent vector is $\mathbf{r}'(t)=(-10\sin t,10\cos t,0)$. The dot product $\mathbf{W}\cdot\mathbf{r}'(t)=2(-10\sin t)= -20\sin t$. Integrate:
\[\int_0^{2\pi}-20\sin t\,dt=20(\cos t)\Big|_0^{2\pi}=0.\]
So over a full loop the wind does no net work.

**🌳 Intermediate:** The drone logs a path from $(0,0,0)$ to $(5,5,0)$ in a straight line, still facing wind $\mathbf{W}=(2,0,0)$. Now compute the work using its sampled data every second. Treat each second as a linear segment, or directly use the line integral of the straight path. Show the advantage of the integral approach.

*Solution:* The straight path has $\mathbf{r}(t)=(t,t,0)$ for $0\le t\le5$. Then $\mathbf{r}'(t)=(1,1,0)$ and $\mathbf{W}\cdot\mathbf{r}'(t)=2\times1=2$. The work is
\[\int_0^5 2\,dt=10\,\text{J (up to a constant scale)}.\]
With discrete segments from the log, we'd sum $2\Delta t$ five times, reaching the same result but with more bookkeeping. The integral unifies it elegantly.

## Meta-Reflection
Line and surface integrals build on single-variable integration 📈 and prepare us for flux-based laws in vector calculus (think Gauss or Stokes). This chapter’s drone theme will later reappear when we discuss numerical methods 🔧 for simulating flight paths.

