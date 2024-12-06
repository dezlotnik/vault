---
id: Value Iteration
aliases:
  - Value Iteration
  - value iteration
tags: []
---

# Value Iteration

> [!definition] Value Iteration
> Value iteration is an algorithm that directly computes the
> optimal value function, $V^*$, of a [[Markov Decision Process]]
> without explicitly representing a policy. It iteratively
> updates the value function for all states until convergence. 
> 
> **Steps:**
> 1. **Initialization:**
>    - Initialize the value function, $V(s)$, for all states $s$.
> 2. **Value Update:**
>    - For each state $s$, update its value using the Bellman optimality equation:
>      $$V(s) \leftarrow \max_a \left[ r(s, a) + \gamma \sum_{s' \in S} p(s'|s,a) V(s') \right]$$
> 3. **Repeat:**
>    - Repeat step 2 until the value function converges, i.e., the changes in the values are negligible.
> Once the optimal value function is obtained, the optimal policy can be derived by choosing the action that maximizes the expected return from each state:
> 
> $$\pi^*(s) = \underset{a \in A}{\operatorname{argmax}} \left[ r(s, a) + \gamma \sum_{s' \in S} p(s'|s,a) V^*(s') \right]$$

## Proof of Convergence

The proof follows from the fact that the [[Bellman Backup Operator|Bellman backup operator]]
is a [[Contraction|contraction mapping]].

From above, the value iteration algorithm iteratively applies the Bellman
backup operator to the current guess for the value function:
$$
V_{k+1} = TV_{k}.
$$

Let $V^*$ denote the optimal value function, this is the fixed point of the
[[Bellman Equation]], $TV^* = V^*$.
Then consider what happens to the distance between the current guess and the
optimal value function under iterative applications of the Bellman backup
operator.

First, due to the contraction mapping property of $T$,
$$
\begin{aligned}
|TV_k - TV^*| & \le \gamma |V_k - V^*|.
\end{aligned}
$$

This implies that

$$
\begin{aligned}
|V_{k+1} - V^*| & \le \gamma |V_k - V^*|.
\end{aligned}
$$

and consequently,

$$
\begin{aligned}
|V_{k} - V^*| & \le \gamma^k |V_0 - V^*|.
\end{aligned}
$$

Therefore, as $k \rightarrow \infty$, $|V_{k} - V^*| \rightarrow 0$.
