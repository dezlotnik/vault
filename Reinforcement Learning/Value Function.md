---
id: Value Function
aliases:
  - Value Function
tags: []
---

# Value Function

The value function, denoted as $V^\pi(s)$, estimates the expected discounted
sum of rewards starting from a given state $s$ and following a specific policy
$\pi$.

> [!definition] Value Function
> The function $V^\pi: S \rightarrow \mathbb{R}$, called the value function, is
> $$
> \begin{aligned}
> V^\pi(s) = r(s,\pi(s)) + \gamma \sum_{s^\prime \in S} p(s^\prime | s, \pi(s)) V^\pi(s^\prime)
> \end{aligned}
> $$
> where $\pi$ is some *stochastic* policy, $\gamma$ is the discount
> factor, $p$ is the
> transition probability function, and $r$ is the immediate reward.

> [!definition] Value Function (Stochastic Policy)
> The function $V^\pi: S \rightarrow \mathbb{R}$, called the value function, is
> $$
> \begin{aligned}
> V^\pi(s) = \sum_{a \in A} \pi(a|s) \left[ r(s,a) + \gamma \sum_{s^\prime \in S} p(s^\prime | s,a) V^\pi(s^\prime) \right]
> \end{aligned}
> $$
> where $\pi$ is some *stochastic* policy, $\gamma$ is the discount
> factor, $p$ is the
> transition probability function, and $r$ is the immediate reward.

## Related
- [[Markov Decision Process]]
- [[Partially Observable Markov Decision Process]]
- [[Reinforcement Learning]]
- [[Q Function|Q Function]]
