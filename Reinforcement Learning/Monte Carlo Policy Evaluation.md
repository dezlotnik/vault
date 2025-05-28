---
id: Monte Carlo Policy Evaluation
aliases:
  - Monte Carlo Policy Evaluation
  - MC Policy Evaluation
  - MC policy evaluation
tags: []
---

# Monte Carlo Policy Evaluation

Monte Carlo policy evaluation is a technique used in reinforcement learning to
estimate the value function of a given policy. It involves simulating multiple
episodes of interaction with the environment and averaging the returns obtained
from each episode.

**Key Concepts:**

* **Episode:** A sequence of states, actions, and rewards that starts from an
initial state and ends in a terminal state.
* **Return:** The sum of discounted rewards obtained in an episode.
* **Value Function:** The expected return from a state under a specific policy.

**Algorithm:**

1. **Initialize:** Initialize the value function V(s) for all states s.
2. **Simulate Episodes:**
   - Simulate multiple episodes using the given policy π.
   - For each episode:
     - For each state s visited in the episode:
       - Calculate the return $G_t$ from that state.
       - Update the value function using the following update rule:
         $$
         V(s) \leftarrow V(s) + \alpha[G_t - V(s)]
         $$
         where $\alpha$ is the learning rate.
