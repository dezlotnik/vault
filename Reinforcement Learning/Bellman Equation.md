---
id: Bellman Equation
aliases:
  - Bellman Equation
  - Bellman equation
tags: []
---

# Bellman Equation

> [!definition] Bellman Equation ^def-bellman-equation
> The *Bellman equation* relates the value of a state to the
> expected immediate reward and the value of subsequent states.
> It is given by
> $$
>   V(s) = \max_a \left [ r(s,a) + \gamma \sum_{s^\prime \in S} p(s^\prime | s, a) V(s^\prime) \right ].
> $$
