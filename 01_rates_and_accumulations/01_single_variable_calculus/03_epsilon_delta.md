---
title: "ε-δ & continuity"
part: "part 1 – rates & accumulations"
chapter: "chapter 1 – single-variable calculus"
section: "sec 1.3 – ε-δ & continuity"
path: "01_rates_and_accumulations/01_single_variable_calculus/03_epsilon_delta.md"
dataset: "covid_daily_cases.csv"
tags: ["📈", "dataset:covid", "level:starter"]
---

## Mini-Hook
Imagine tracking daily COVID-19 cases using `/datasets/covid_daily_cases.csv`, which lists `date` and `cases` columns. The raw numbers sway up and down, but a logistic curve with growth rate `r = 0.25` and carrying capacity `K = 100000` seems to fit the trend. You want to know **exactly** when the predicted counts settle down and whether tiny changes in time lead to tiny changes in cases. Continuity answers that.

## Intuition
Think of a faucet—you turn the knob a little and the water flow changes a little. That "little in, little out" feeling underpins the $ε$–$δ$ idea. If you zoom way in on a nice smooth curve, it looks almost straight; move your finger along by a teeny amount $δ$, and the height only wiggles by a teeny amount $ε$. The logistic curve is smooth in that sense: slide time `t` slightly, and the predicted case count barely budges.

## Formal Core
**Definition (Limit).** We say $\lim_{x\to c} f(x) = L$ if for every $\epsilon>0$ there exists a $\delta>0$ such that whenever $0 < |x-c| < \delta$, we have $|f(x)-L| < \epsilon$.
*Why care?* This nails down what it means for $f(x)$ to get arbitrarily close to $L$ as $x$ approaches $c$, avoiding hand-wavy notions of "getting near."

**Definition (Continuity).** A function $f$ is continuous at $c$ if $\lim_{x\to c} f(x) = f(c)$.
*Why care?* Continuity guarantees that small input tweaks cause only small output changes—vital when trusting predictions from data.

**Example (Logistic Continuity).** The logistic function
$$L(t)=\frac{K}{1+Ae^{-rt}}$$
with constants $K>0$, $A>0$, and $r>0$ is continuous for all real $t$. Applying the limit definition to any point $t_0$ shows that for every $\epsilon$ you can find a $\delta$ depending on $\epsilon$, $K$, $A$, and $r$, ensuring $|L(t)-L(t_0)|<\epsilon$ whenever $|t-t_0|<\delta$.

## Worked Problems
**🌱 Problem.** Show that $f(x)=x^2$ is continuous at $x=3$ using the $ε$–$δ$ definition.

**Solution.** Let $\epsilon>0$. Choose $\delta=\min\{1,\epsilon/7\}$. Then if $|x-3|<\delta$, we have $|x|<4$ and
$$|x^2-9| = |x-3||x+3| < \delta(7) \le \epsilon.$$ Thus $f(x)$ is continuous at 3.

**🌳 Problem.** Verify continuity of $L(t)=\frac{K}{1+Ae^{-rt}}$ at an arbitrary point $t_0$.

**Solution.** Let $\epsilon>0$. Because exponentials are continuous, there exists $\delta$ so that $|e^{-rt}-e^{-rt_0}|<\frac{\epsilon A e^{-rt_0}}{K}$ whenever $|t-t_0|<\delta$. Multiplying through shows
$$|L(t)-L(t_0)| = \frac{K A e^{-rt_0}|e^{-r(t-t_0)}-1|}{(1+Ae^{-rt})(1+Ae^{-rt_0})} < \epsilon.$$
Hence $L(t)$ is continuous at $t_0$.

## Meta-Reflection
Continuity cements the intuition from the previous section on limits and sets the stage for derivatives next. The logistic model's smoothness means we can safely take slopes to estimate growth rates (📈), and later we'll integrate to tally total infections. For a peek ahead: solving for $r$ via Newton's method will push these ideas even further.
