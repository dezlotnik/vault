---
id: Optimal Control Problem Statement
aliases:
  - Optimal Control Problem Statement
tags: []
---

# Optimal Control Problem Statement

[[Dynamic Programming for Optimal Control]]

#### Continuous Time Finite Horizon

> [!definition] Continuous Time Optimal Control Problem
> $$
> \begin{aligned}
>	& \text{min}_u \ J  = \phi(x(t_f), t_f) + \int_{t_0}^{t_f} \ell(x(t), u(t),
>        t) \mathrm{d}t \\
>	& \text{subject to} \ \dot{x} = f(x, u, t)
> \end{aligned}
> $$ 
> ^continuous-time-optimal-control

#### Discrete Time Finite Horizon

> [!definition] Discrete Time Optimal Control Problem
> $$
> \begin{aligned}
> 	& \text{min}_u \ J  = \phi(x(N)) + \sum_{k=0}^{N} \ell(x(k), u(k)) \\
> 	& \text{subject to} \ x(k+1) = f(x(k), u(k))
> \end{aligned}
> $$
