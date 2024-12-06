---
id: Policy Iteration
aliases:
  - Policy Iteration
tags: []
---

# Policy Iteration

Policy Iteration is a method for computing the optimal policy for a
[[Markov Decision Process]]. This is done by iteratively updating the control
policy. Unlike [[Value Iteration|value iteration]], at each step in the
iteration the new policy is guaranteed to improve on the previous, unless it is
already optimal.

> [!definition] Policy Iteration
>
> Policy iteration is a reinforcement learning algorithm that iteratively improves a policy by alternating between two steps: policy evaluation and policy improvement.
> 
> **Steps:**
> 
> 1. **Policy Evaluation:**
>    - Given a policy $\pi$, compute its value function $V^\pi(s)$ for all states $s$.
> 2. **Policy Improvement:**
>    - Improve the policy by acting greedily with respect to the current value function. This means selecting the action that maximizes the expected return from the current state:
> $$
> \begin{aligned}
> \pi'(s) & = \underset{a \in A}{\operatorname{argmax}} \left[ r(s, a) + \gamma \sum_{s' \in S} p(s'|s,a) V^\pi(s') \right] \\
>         & = \underset{a \in A}{\operatorname{argmax}} \  Q^\pi(s,a)
> \end{aligned}
> $$
> where $Q^\pi$ is the [[Q Function|state-action value function]].
> 3. **Repeat:**
>    - Repeat steps 1 and 2 until the policy converges, i.e., no further improvement is possible.

Policy iteration guarantees convergence to the optimal policy in a finite number
of iterations for finite MDPs.

## Proof of Convergence
