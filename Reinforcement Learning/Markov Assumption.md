---
id: Markov Assumption
aliases:
  - Markov Assumption
tags: []
---

# Markov Assumption

The Markov Assumption states that the future state of a system depends only
on its present state, not on past states.

In other words, the state is a *sufficient statistic* of history.

> [!definition] Markov Property
> A [[stochastic process]], $\{s_t\}_{t \in \mathbb{N}}$, is said
> to have the Markov Property if the conditional probability distribution of
> future states of the process, given the present state, is independent of past
> states.
> 
> The property can be expressed as
> $p(s_{t+1} | h_t) = p(s_{t+1} | s_t)$
> where $h_t$ is the history.

> [!tip] Main idea
> The future is independent of the past, given the current state.
