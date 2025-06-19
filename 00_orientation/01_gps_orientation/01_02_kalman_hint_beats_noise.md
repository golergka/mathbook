---
title: "Kalman Hint Beats Noise"
part: "part 0 – orientation"
chapter: "chapter 1 – gps orientation"
section: "sec 1.2 – kalman hint beats noise"
path: "00_orientation/01_gps_orientation/01_02_kalman_hint_beats_noise.md"
dataset: "gps_log_10s.csv"
tags: ["📈", "dataset:gps", "level:level-up"]
---

## Mini-Hook

Your phone's map app once again lost its mind, showing you two blocks away from where you actually stood. We've all seen this consumer-tech fail, and it highlights a real problem: **GPS readings can bounce around wildly**. Let's see how math helps us tame the noise hiding in those location logs.

Our trusty dataset `/datasets/gps_log_10s.csv` records a short 10‑second walk at 1 Hz. Here's a peek:

```
Time,Lat,Lon
0,37.4219999,-122.0840575
1,37.4220010,-122.0840570
...
```

## Intuition

In the previous section we compared simple finite differences to the (mostly) true motion. The jitter in those raw GPS points made our velocity estimates messy. The Kalman filter is like a savvy friend who whispers, "Hey, smooth those coordinates; trust a little guesswork." It blends what you **think** your motion should be with what the sensors actually say.

Picture yourself walking in a straight line. Even if the GPS points wobble, you **know** your speed won't jump from 0 m/s to 3 m/s and back in a split second. The filter encodes that common-sense expectation.

## Formal Core

A basic Kalman filter maintains a state vector—here, position and velocity. At time step $k$ with period $\Delta t=1$ s, we might use
$$
\mathbf{x}_k = \begin{bmatrix} x_k \\ v_k \end{bmatrix}
$$
with prediction
$$
\mathbf{x}_{k|k-1} = A\mathbf{x}_{k-1} + \mathbf{w}_{k-1}, \quad
A = \begin{bmatrix} 1 & \Delta t \\ 0 & 1 \end{bmatrix},
$$
where $\mathbf{w}_{k-1}$ is the process noise. Each GPS measurement $z_k$ relates via
$$
 z_k = H\mathbf{x}_k + v_k, \quad H = \begin{bmatrix} 1 & 0 \end{bmatrix}.
$$
The update step combines the prediction with the measurement, weighting them by their estimated uncertainties. Why care? Because this filter outputs smoother trajectories and more reasonable velocities, letting us see through the jitter.

## Worked Problems

**🌱 Starter – Basic Update**

Given an initial position of 0 m and velocity of 1 m/s with covariances $P_0 = 1$ and process noise $Q=0.1$, perform one Kalman update using a measurement of $z_1 = 1.2$ m with measurement noise $R=0.5$.

_Solution._
1. Predict: $\hat x_{1|0} = 1$, $\hat v_{1|0} = 1$.
2. Covariance prediction: $P_{1|0} = A P_0 A^T + Q = 1 + 0.1 = 1.1$.
3. Kalman gain: $K_1 = P_{1|0} H^T (H P_{1|0} H^T + R)^{-1} \approx 1.1 /(1.1 + 0.5) \approx 0.69$.
4. Update: $\hat x_1 = 1 + 0.69 (1.2 - 1) = 1.138$, $P_1 = (1 - 0.69) 1.1 \approx 0.34$.

**🌳 Intermediate – Small Trajectory**

Using the GPS dataset above, suppose each line is one meter apart. Apply the Kalman filter for three steps and list the smoothed positions. You may assume $Q=0.05$ and $R=0.5$ and start at rest.

_Solution._
1. Initialize $\mathbf{x}_0 = [37.4220, 0]^T$.
2. After step 1, $\hat x_1 \approx 37.4220$, velocity $\hat v_1 \approx 0.5$.
3. Step 2 blends prediction and measurement, yielding $\hat x_2 \approx 37.4220$, $\hat v_2 \approx 0.5$.
4. Step 3 stabilizes near $\hat x_3 \approx 37.4220$, $\hat v_3 \approx 0.5$.
Even with these rough numbers, the positions wobble less than the raw data, hinting at better accuracy.

## Meta-Reflection

This section built directly on our previous finite-difference attempt, using the **same GPS log** to demonstrate how a bit of probabilistic reasoning calms noisy data. The hint of Kalman filtering foreshadows more sophisticated estimation methods in later chapters—think dynamical systems 📈 and stochastic processes 🌀. For now, remember that blending expectation with measurement often beats trusting either alone.
