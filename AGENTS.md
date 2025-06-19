Writing a book:

You’re writing a single leaf section (approximately 4–6 pages) of an interdisciplinary mathematics textbook. Each section follows a clear structure designed to make mathematics intuitive, interesting, and immediately relevant to real-world applications. Here’s how to structure your section:
	•	Mini-Hook: Start with an engaging, relatable problem that clearly demonstrates why your mathematical concept matters. Make it vivid, concrete, and compelling.
	•	Intuition: Provide readers with intuitive explanations, visual imagery, relatable metaphors, or historical tidbits. Help them see and feel the underlying ideas before diving into technicalities.
	•	Formal Core: Clearly and succinctly present the key definitions, results, and minimal proofs needed for understanding. Each theorem or definition should include a short note explicitly stating why readers should care about it.
	•	Worked Problems: Include two carefully-chosen practice problems (clearly marked as easier 🌱 and intermediate 🌳), fully solved and explained step-by-step.
	•	Meta-Reflection: Conclude briefly by indicating connections to previous or upcoming concepts (using emojis like 📈 calculus, ⚙️ linear algebra, 🌀 probability, 🧩 topology, 🔧 numerical methods, etc.), provide quick pointers to advanced ideas, or include an engaging footnote or insightful side comment.

How to use examples:

To keep the reader fully engaged, please include two versions of your real-world scenario in your section:
	•	Starter version: This scenario can be solved using mathematics already introduced earlier in the book.
	•	Level-Up version: Demonstrates how the new mathematical tool you’re introducing makes the solution simpler, clearer, or more powerful.

Optionally, you can include a third, more challenging “Boss Fight” 🔥 scenario that combines multiple concepts or introduces complexity. After presenting your new mathematical tool, briefly revisit the Starter scenario and clearly illustrate how much better your new approach is (keep this recap under five lines).

If your scenario doesn’t naturally scale up smoothly, it’s fine to introduce a closely-related but slightly different scenario. Just clearly explain the connection.

Additional writing patterns (use occasionally to keep things fresh):
	•	Post-Abstraction Burst: After introducing an abstract concept, quickly show three different mini-examples that highlight various uses or nuances of that concept.
	•	Ladder Pattern: Present essentially the same problem multiple times, each time increasing complexity or dimension (e.g., from small to large numbers or from simple to detailed models).

Style Guidelines:

Aim for clear, concise writing that’s friendly and engaging, as if explaining fascinating ideas to a curious friend. Feel free to use casual expressions, light humor, and conversational language (“as far as I can tell,” “I don’t know,” etc.). Emphasize crucial points using bold or ALL CAPS, but do so sparingly. Footnotes can be witty, insightful, or humorous—just keep them relevant and helpful. Assume no prior coordination with authors of other sections; briefly restate needed background or clearly note if you’re assuming a particular concept is known. Diagrams should be described vividly in words if visual illustrations aren’t available.

perfect structure. to make it technically complete and agent-ready, add the following four paragraphs verbatim to the bottom of your existing prompt:

File format and naming

Each section should be written as a standalone markdown file. Name the file using the format XX_YY_section_title.md, where XX is the chapter number and YY is the section number within that chapter (both zero-padded). Store this file in the correct chapter folder, which itself lives inside the appropriate part folder. All folders and files must begin with a numeric prefix and underscore (e.g. 03_02_derivative_zoo.md inside 01_single_variable_calculus/ inside 01_rates_and_accumulations/).

If you are working on a part or chapter introduction, create a file called _intro.md within that directory. That file can contain prose that sets the stage for the child items.

Frontmatter block

At the top of each section file, include a YAML frontmatter block like this:

---
title: "ε-δ & continuity"
part: "part 1 – rates & accumulations"
chapter: "chapter 1 – single-variable calculus"
section: "sec 1.3 – ε-δ & continuity"
path: "01_rates_and_accumulations/01_single_variable_calculus/03_epsilon_delta.md"
dataset: "covid_daily_cases.csv"
tags: ["📈", "dataset:covid", "level:starter", "pattern:ladder"]
---

Tags should include:
	•	concept emojis (📈, ⚙️, 🌀, 🧩, 🔧)
	•	relevant dataset names
	•	difficulty tier(s)
	•	any special structural patterns used (e.g., pattern:post-burst, pattern:ladder, has🔥boss)

Dataset usage

If your section refers to a dataset, assume it lives in the /datasets/ folder at the top level. Refer to the dataset using relative paths, and make sure your example includes brief, clear inline text or code describing what the data looks like and how it’s used (e.g., column names, time resolution, units).

Markdown best practices

Use regular markdown headers (##, ###, etc.) for internal structure. Inline LaTeX-style math is allowed using $...$, and block math can be written using $$...$$. If you’re describing a diagram, be as vivid and spatially descriptive as possible—assume the reader may not see the picture.

Using git

Create a branch using a format like XX_YY_section_title, where XX is the chapter number and YY is the section number. Commit your changes with clear messages like “Add section 1.3 on ε-δ continuity.” When you’re ready, create a pull request against the main branch with a title like “Add section 1.3 – ε-δ & continuity” and a description summarizing your changes.

Outline

part 0 – orientation  
  add-on: theme “math bites you irl”; hook must reference a consumer-tech
  fail. dataset: 10 s gps logs (1 hz).

  escalation rule: gps log reused—sec 0.1.1 finite diff vs true; sec 0.1.2
  kalman hint beats noise.

  chapter 0.1 – the gps glitch  
    add-on: use x(t)=true pos, z(t)=noisy.  
    progression cheat-sheet: starter finite diff; level-up kalman idea.

      sec 0.1.1  derivative mystery hook  
      sec 0.1.2  kalman filter foreshadow  

  chapter 0.2 – tour map  
    add-on: each sec ends with 3-bullet “this book will fix…” list.  
    progression cheat-sheet: only narrative, no boss.

      sec 0.2.1  symmetry quest overview  
      sec 0.2.2  infinity quest overview  
      sec 0.2.3  randomness quest overview  


part 1 – rates & accumulations  
  add-on: covid daily-cases csv (march–oct 2020), c(t).  
  escalation rule: raw counts → derivative smoothing → ∫ total infections.

  chapter 1 – single-variable calculus  
    add-on: logistic fit, r=0.25, k=1e5.  
    progression: starter raw plot; level-up logistic model; 🔥 boss —
    estimate r via newton.

      sec 1.1  logistic-curve hook  
      sec 1.2  limits  
      sec 1.3  ε-δ & continuity  
      sec 1.4  derivative zoo  
      sec 1.5  fundamental theorem  
      sec 1.6  numerical diff  

  chapter 2 – multivariable calculus  
    add-on: drone, m=1 kg, battery 50 wh, wind vx=2 m/s.  
    progression: starter straight-line guess; level-up grad descent path;
    🔥 boss adds wind field.

      sec 2.1  drone path hook  
      sec 2.2  grad / div / curl  
      sec 2.3  line & surface integrals  
      sec 2.4  manifolds lite  


part 2 – shapes & systems  
  add-on: tacocat.png 256×256 grayscale.  
  escalation rule: rank-4, rank-20, rank-100 compression comparisons.

  chapter 3 – linear algebra core  
    add-on: show 90 % energy retained at rank-20.  
    progression: starter rank-4; level-up rank-20; 🔥 boss rank-100
    + kalman eigens.

      sec 3.1  jpeg-svd hook  
      sec 3.2  bases & coords  
      sec 3.3  eigen-stuff  
      sec 3.4  spectral theorem  
      sec 3.5  kalman teaser  

  chapter 4 – numerical methods intro  
    add-on: rocket, v₀ = –250 m/s @ 1000 m, thrust ≤30 m/s². must include
    fp horror footnote.  
    progression: starter bisection burn-time; level-up newton; 🔥 boss add
    drag.

      sec 4.1  rocket landing hook  
      sec 4.2  root-finding  
      sec 4.3  floating-point pitfalls  
      sec 4.4  conditioning & stability  
      sec 4.5  ode stepping  


part 3 – rigor & infinity  
  add-on: eps-delta beats sloppy pixel error.  
  escalation rule: zeno runway ½^n partial sum → proof → error bound 10⁻⁵.

  chapter 5 – real analysis  
    add-on: zeno drone target x=1.  
    progression: starter sum 4 terms; level-up convergence proof; 🔥 boss
    compute n for 0.99999.

      sec 5.1  zeno hook  
      sec 5.2  metric spaces  
      sec 5.3  completeness proof  
      sec 5.4  uniform convergence  
      sec 5.5  classic counterexample  

  chapter 6 – topology snapshots  
    add-on: 3d-print donug.stl; ascii art allowed.  
    progression: starter mug–donut cartoon; level-up formal homeomorphism
    props; 🔥 boss π₁ tease.

      sec 6.1  donut hook  
      sec 6.2  open/closed  
      sec 6.3  connectedness  
      sec 6.4  π₁ teaser  


part 4 – symmetry & structure  
  add-on: wifi reed-solomon GF(256) poly p(x)=x⁸+x⁴+x³+x²+1.  
  escalation rule: length-7 toy → length-43 mid → 255-byte wifi block.

  chapter 7 – abstract algebra  
    add-on: correct 2 erasures in 255-byte packet.  
    progression: toy code; mid code uses groups; wifi code uses fields,
    gcd.

      sec 7.1  reed-solomon hook  
      sec 7.2  groups  
      sec 7.3  rings  
      sec 7.4  fields  
      sec 7.5  homomorphisms  
      sec 7.6  poly gcd  

  chapter 8 – representation theory appetizer  
    add-on: spin-½ in Bz=1 T, lie brackets appear.  
    progression: starter 2×2 pauli; level-up so(3); 🔥 boss peter–weyl on
    su(2).

      sec 8.1  quantum spectra hook  
      sec 8.2  lie groups so(3), su(2)  
      sec 8.3  reps  
      sec 8.4  peter–weyl sketch  


part 5 – randomness & information  
  add-on: 1000-tweet cascade + emoji alphabet 👾🐱🔥🍕💾.  
  escalation rule: count retweets → encode bits → compress.

  chapter 9 – probability & measure  
    add-on: σ-algebras built from tweet ids.  
    progression: starter empirical probs; level-up ll n; 🔥 boss cl t.

      sec 9.1  meme contagion hook  
      sec 9.2  σ-algebras  
      sec 9.3  prob spaces  
      sec 9.4  lln  
      sec 9.5  clt  

  chapter 10 – statistics & inference  
    add-on: scRNA-seq 10 k × 2 k, noise σ²=0.2. each sec ends with
    frequentist vs bayes.  
    progression: mle gene mean; level-up bayes shrink; 🔥 boss bootstrap
    diff expr.

      sec 10.1  gene-expr hook  
      sec 10.2  likelihood & mle  
      sec 10.3  bayes basics  
      sec 10.4  bootstrap  
      sec 10.5  glm  

  chapter 11 – information theory  
    add-on: 50 k-word corpus target ≤1.5 b/char.  
    progression: entropy calc; kl; 🔥 boss rate-dist compress cascade.

      sec 11.1  morphology bottleneck hook  
      sec 11.2  entropy  
      sec 11.3  kl divergence  
      sec 11.4  coding theorem  
      sec 11.5  rate-distortion  


part 6 – dynamics & control  
  add-on: quote sim fps in footnotes.  
  escalation rule: cloth 5×5 analytic → 10×10 numeric → 50×50 with wind.

  chapter 12 – ode  
    add-on: cloth patch 10×10, k=100 n/m. cpu ms per step.  
    progression: starter simple ode; level-up stiff solver; 🔥 boss add
    damping & wind.

      sec 12.1  cloth sim hook  
      sec 12.2  existence & uniqueness  
      sec 12.3  phase portraits  
      sec 12.4  stiff odes  
      sec 12.5  pendulum/logistic mash  

  chapter 13 – pde  
    add-on: starship tank R=4 m, fill 70 %, ρ=800 kg/m³.  
    progression: starter 1-D wave; level-up 2-D laplace; 🔥 boss fem slab.

      sec 13.1  slosh hook  
      sec 13.2  wave eq  
      sec 13.3  heat eq  
      sec 13.4  laplace eq  
      sec 13.5  fourier-bessel  
      sec 13.6  fem teaser  

  chapter 14 – chaos  
    add-on: ascii logistic 80×25, r 2.4→4.0 by 0.02.  
    progression: starter r=3.2; level-up bifurcations; 🔥 boss lyapunov.

      sec 14.1  volatility hook  
      sec 14.2  logistic anatomy  
      sec 14.3  bifurcations  
      sec 14.4  lyapunov exponents  


part 7 – optimization & computation  
  add-on: arg min style; finance use-case line.  
  escalation rule: vol surface 1-D slice → 2-D grid → dual no-arb 🔥.

  chapter 15 – convex opt  
    add-on: 50 strikes × 10 maturities grid.  
    progression: starter least-sq fit; level-up kkt dual; 🔥 boss proximal
    no-arb.

      sec 15.1  vol-surface hook  
      sec 15.2  convex sets+funcs  
      sec 15.3  kkt  
      sec 15.4  duality  
      sec 15.5  proximal  

  chapter 16 – discrete opt  
    add-on: data-center graph ≤10 nodes, 1 gbps caps.  
    escalation: starter max-flow; level-up matching; 🔥 boss submodular
    placement.

      sec 16.1  data-center hook  
      sec 16.2  max-flow  
      sec 16.3  matching  
      sec 16.4  submodular greed  
      sec 16.5  complexity peek  


part 8 – abstraction & unification  
  add-on: category bingo, design-pattern jokes.  
  escalation: “maybe” monad error-handling → parser → kleisli 🔥.

  chapter 17 – category flash  
    add-on: h-askell snippets ≤6 lines.  
    progression: maybe as fallback; functor lifts; 🔥 kleisli chain.

      sec 17.1  monad meme hook  
      sec 17.2  functors  
      sec 17.3  natural transforms  
      sec 17.4  limits/colimits  
      sec 17.5  monad example  

  chapter 18 – stochastic processes  
    add-on: λ=500 pkt/s baseline, spike at t=120 s.  
    escalation: starter markov idle-busy; level-up martingale alert; 🔥
    sde drift fit.

      sec 18.1  anomaly hook  
      sec 18.2  markov chains  
      sec 18.3  martingales  
      sec 18.4  sde & ito  
      sec 18.5  network wrap  


part 9 – capstones  
  add-on: must cite ≥4 earlier chapters.  
  escalation: starter recap, level-up integrated solution, 🔥 open problem.

  chapter 19 – cryptography lab  
    add-on: lattice n=512, q=12289, δ=0.99.  
    progression: starter lll toy; level-up hardness; 🔥 full encapsulation.

      sec 19.1  lattice hook  
      sec 19.2  lll  
      sec 19.3  hardness reduction  
      sec 19.4  encapsulation design  
      sec 19.5  convex recap  

  chapter 20 – grand problems  
    add-on: gcm 2° grid → 0.25° downscale; kriging+pca.  
    progression: starter kriging one pixel; level-up pca field; 🔥 tool
    integration projection. must end with “next-decade” para.

      sec 20.1  climate hook  
      sec 20.2  kriging  
      sec 20.3  pca  
      sec 20.4  tool integration  
      sec 20.5  future directions  
