---
id: Bellman Backup Operator
aliases:
  - Bellman Backup Operator
  - Bellman backup operator
tags: []
---

# Bellman Backup Operator

> [!definition] Bellman Backup Operator ^def-bellman-backup
> The Bellman backup operator, often denoted as $T$, is an 
> operator that updates the [[Value Function|value function]] of a state by
> considering the expected future reward. It's derived from the
> Bellman equation.
>
> Given a value function $V^\pi$, the Bellman backup operator $T$, maps the value
> function to a new function $TV^\pi: S \rightarrow \mathbb{R}$ given by:
> $$
> \begin{aligned}
>  TV^\pi(s) & = \max_a \sum_{a \in A} \pi(a | s) \left[ r(s,a) + \gamma \sum_{s^\prime \in S} p(s^\prime | s,a) V^\pi(s^\prime) \right],
> \end{aligned}
> $$
>
> assuming stochastic actions. Or, assuming deterministic actions:
>
> $$
> \begin{aligned}
>  TV^\pi(s) & = \max_a \left[ r(s,a) + \gamma \sum_{s^\prime \in S} p(s^\prime | s,a) V^\pi(s^\prime) \right].
> \end{aligned}
> $$

The [[Bellman Equation]] can be understood as a fixed point of the Bellman
backup operator, i.e.,
$$
TV^\pi = V^{\pi}.
$$

The Bellman backup operator can also be used to prove convergence of the
[[Value Iteration|value iteration]] algorithm. Specifically, proof follows due
to the fact that the Bellman backup operator is a [[Contraction|contraction mapping]].

## Proof that the Bellman Backup is a Contraction

Recall, a contraction mapping is defined as 

![[Contraction#^def-contraction-mapping]]

To prove that the Bellman backup operator is a contraction mapping, consider
two value function $V_1$ and $V_2$. The Bellman backup operator is a
contraction if
$$
|TV_1 - TV_2| \le \alpha |V_1 - V_2|,
$$
for some $\alpha \in [0, 1)$.

$$
\begin{aligned}
    |TV_1 - TV_2| & = | \max_a \left[ r(s,a) + \gamma \sum_{s^\prime \in S} p(s^\prime | s,a) V_1^\pi(s^\prime) \right] - \max_a \left[ r(s,a) + \gamma \sum_{s^\prime \in S} p(s^\prime | s,a) V_2^\pi(s^\prime) \right] | \\
    & = | \max_a \gamma \sum_{s^\prime \in S} p(s^\prime | s,a) V_1^\pi(s^\prime) - \max_a \gamma \sum_{s^\prime \in S} p(s^\prime | s,a) V_2^\pi(s^\prime) | \\
    & \le \gamma | \max_a \sum_{s^\prime \in S} p(s^\prime | s,a) \left [  V_1^\pi(s^\prime) - V_2^\pi(s^\prime)  \right ] | \\
    & \le \gamma \max_a \sum_{s^\prime \in S} p(s^\prime | s,a) | \left [  V_1^\pi(s^\prime) - V_2^\pi(s^\prime)  \right ] | \\
    & \le \gamma |  V_1^\pi(s^\prime) - V_2^\pi(s^\prime) |.
\end{aligned}
$$

This proves the Bellman backup operator is a contraction mapping, provided
the discount factor $\gamma$ is less than $1$.
