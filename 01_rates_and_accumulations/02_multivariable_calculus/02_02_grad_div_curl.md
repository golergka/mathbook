---
title: "grad, div & curl"
part: "part 1 – rates & accumulations"
chapter: "chapter 2 – multivariable calculus"
section: "sec 2.2 – grad, div & curl"
path: "01_rates_and_accumulations/02_multivariable_calculus/02_02_grad_div_curl.md"
dataset: "covid_daily_cases.csv"
tags: ["📈", "dataset:covid", "level:level-up", "pattern:post-burst"]
---

## Mini-Hook

Imagine piloting a $1\,\text{kg}$ drone with a $50\,\text{Wh}$ battery on a breezy afternoon. The wind blows steadily east at $2\,\text{m/s}$, threatening to push your drone off its planned straight-line path. Starter approach? Just aim directly at the destination and hope for the best. Level-Up version? Treat the wind as a vector field and analyze how it nudges the drone at every point in space. That's where the trio of **gradient**, **divergence**, and **curl** come to the rescue.

## Intuition

Think of a hilly landscape as a smooth sheet. The **gradient** at any point is like an arrow pointing straight uphill—steeper hills mean longer arrows. The **divergence** measures how much a field spreads out from a point, like water gushing from a spring. And the **curl** captures swirling behavior, akin to mini tornadoes twisting around a spot. If you’ve ever smoothed the COVID-19 daily case counts from `datasets/covid_daily_cases.csv`, you’ve already computed a one-dimensional gradient—these ideas simply extend that notion to two or three dimensions.

## Formal Core

**Definition (Gradient).** For a scalar function $f(x,y,z)$, the gradient is
$$\nabla f = \left(\frac{\partial f}{\partial x},\frac{\partial f}{\partial y},\frac{\partial f}{\partial z}\right).$$
*Why care?* The gradient points in the direction of steepest increase of $f$, crucial when optimizing paths or energies.

**Definition (Divergence).** For a vector field $\mathbf{F}=(F_x,F_y,F_z)$,
$$\nabla\cdot\mathbf{F}=\frac{\partial F_x}{\partial x}+\frac{\partial F_y}{\partial y}+\frac{\partial F_z}{\partial z}.$$
*Why care?* Divergence quantifies sources and sinks—useful for tracking how wind flows compress or expand near your drone.

**Definition (Curl).** For the same vector field,
$$\nabla\times\mathbf{F}=\left(
\frac{\partial F_z}{\partial y}-\frac{\partial F_y}{\partial z},
\frac{\partial F_x}{\partial z}-\frac{\partial F_z}{\partial x},
\frac{\partial F_y}{\partial x}-\frac{\partial F_x}{\partial y}
\right).$$
*Why care?* Curl detects swirling motion in the field—key for understanding vortices that could spin the drone.

### Post-Abstraction Burst

1. **Temperature Map.** The gradient of a temperature field shows the direction of fastest warming.
2. **Crowd Density.** Divergence of a crowd flow field pinpoints where people are packing in or dispersing.
3. **Ocean Currents.** Curl highlights eddies that trap debris.

## Worked Problems

**🌱 Easier.** *Gradient of a Hill.*
Suppose the terrain height is $h(x,y)=100-0.1x^2-0.05y^2$ (meters). Find the gradient at $(10,5)$ and explain what it means for the drone.

**Solution.**
$$\begin{aligned}
\nabla h &= \left(-0.2x,-0.1y\right).\\
\nabla h(10,5) &= \left(-2,-0.5\right).
\end{aligned}$$
The vector points downhill toward $(2,0.5)$ magnitude, indicating the slope the drone would feel if flying close to the ground. To climb fastest, move opposite this direction.

**🌳 Intermediate.** *Wind Field Divergence.*
Take a simplified wind field $\mathbf{W}(x,y)=(2+y,-x)$. Compute $\nabla\cdot\mathbf{W}$ and interpret the result at $(1,-2)$.

**Solution.**
$$\nabla\cdot\mathbf{W}=\frac{\partial}{\partial x}(2+y)+\frac{\partial}{\partial y}(-x)=0+0=0.$$
At every point, the divergence is zero—the wind neither spreads out nor compresses. At $(1,-2)$, flows merely rotate, so battery drain comes from fighting direction changes, not expansion.

## Meta-Reflection

Gradients generalize single-variable derivatives, bridging this chapter with the logistic curve analysis from [sec 1.1]. Divergence and curl foreshadow line and surface integrals ahead 📈. Curious readers can explore how these tools drive fluid simulation or electromagnetism. Footnote: some drone simulators cap out at $60\,$fps—plenty for practice flights but not quite cinematic.
