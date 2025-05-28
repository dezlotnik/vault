---
id: Temporal Difference Learning
aliases:
  - Temporal Difference Learning
tags: []
---

# Temporal Difference Learning

## TD(0)

TD(0) is a fundamental temporal-difference learning algorithm in
[[Reinforcement Learning]].
It computes the [[Value Function|value function]] of an
[[Markov Decision Process|MDP]] by updating the value estimate of a state based
on the immediate reward and the estimated value of the next state. 

> [!definition] TD(0) Algorithm
> 1. Input: $\alpha$
> 2. Initialize $V^\pi(s) = 0$ for all $s$
> 3. Loop:
> - Sample tuple $(s, a, s^\prime, r)$
> - Update $V^\pi(s) = V^\pi(s) + \alpha \left ( r + \gamma V^\pi(s^\prime) - V^\pi(s) \right )$

