---
id: Q Function
aliases:
  - Q-value
  - Q Value
  - Q value
  - Q function
  - Q Function
  - state-action value function
  - State-Action Value Function
tags: []
---

# Q Function

The $Q$ function, also called the state-action value function, is the expected
discounted sum of rewards when starting in a state, taking an action, and then
following a policy for the remainder of the horizon.

> [!definition] $Q$ Function
> The function $Q^\pi: S \times A \rightarrow \mathbb{R}$, called the $Q$ function or the
> state-action value function, is
> $$
> \begin{aligned}
>     Q^\pi(s,a) = r(s,a) + \gamma \sum_{s^\prime \in S} p(s^\prime | s,a) V^\pi(s^\prime)
> \end{aligned}
> $$
> where $\pi$ is some policy, $V^\pi$ is the value function associated with
> policy $\pi$, $\gamma$ is the discount factor, $p$ is the transition
> probability function, and $r$ is the immediate reward.

The Q function is closely related to the [[Value Function]]. The value function
is the expected discounted sum of rewards by following a policy. The Q
function uses a different action for the immediate step, before following the
policy for the remainder of the horizon.

## Related
- [[Markov Decision Process]]
- [[Partially Observable Markov Decision Process]]
- [[Q Learning]]
- [[Reinforcement Learning]]
- [[Value Function]]
