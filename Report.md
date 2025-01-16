# DQN Methodology (Summary)

## Q-Learning Overview

Q-Learning is a reinforcement learning algorithm where an agent learns to explore an environment by taking actions that change the state of the environment. For each action the agent takes, it receives a reward, which can be:

- **Negative**: when the action is bad;
- **Positive**: when the action is good;
- **Neutral (zero)**: when the action has no significant impact.

The chosen action is based on the highest Q-value, calculated using the **Bellman equation**:

```math
Q(s,a) \gets Q(s,a) + \alpha \left[ r + \gamma \max_{a'} Q(s',a') - Q(s,a) \right]
```

### Where:
- `s`: Current state;
- `a`: Action taken;
- `r`: Reward received;
- `s'`: New state reached after the action;
- `\alpha`: Learning rate;
- `\gamma`: Discount factor, weighting future rewards.

The Q-value represents the expected future reward for taking action `a` in state `s`. These values are stored in a table that maps states to possible actions. However, the main disadvantage of Q-Learning is its **lack of scalability**, as it requires knowledge of all possible states in the environment.

---

## Deep Q-Network (DQN)

DQN addresses the scalability issue of Q-Learning by replacing the Q-value table with a **neural network**. This network:

- Receives the state as **input**;
- Outputs the Q-values for each possible action.

In a **greedy policy**, the action with the highest Q-value is selected. This eliminates the need to know all possible states beforehand.

### Neural Network Functionality in DQN

A neural network in DQN operates as follows:
1. **Input layer**: Receives the state of the environment.
2. **Hidden layers**: Apply weights and activation functions to process the input.
3. **Output layer**: Produces the Q-values for the corresponding actions.

Learning is performed using the **backpropagation method** to minimize the error between predicted and target Q-values.

---

## Improvements to DQN

Despite its efficiency, the simple DQN model is prone to instability. To address this, several improvements have been introduced:

### 1. Target Neural Network
In the simple DQN, updating both the neural network weights and the Q-values simultaneously leads to instability. A **target network** is used to solve this problem:

- The target network has the same architecture as the main network but with weights "frozen" for a few episodes.
- The main network updates its weights based on Q-values provided by the target network.
- Periodically, the weights of the target network are synchronized with those of the main network, improving stability.

### 2. Experience Replay Buffer
To prevent the network from overfitting to sequential patterns in the data, transitions `(s, a, r, s')` are stored in an **experience buffer**:

- Transitions are stored in the buffer.
- During training, random samples from the buffer are used, promoting diversity in the training data and improving efficiency.

---

## Pseudocode for DQN

```plaintext
For episode = 1, M do
    Initialize replay buffer B
    Initialize state s₁ and preprocess ϕ₁ = ϕ(s₁)

    For t = 1, T do
        With probability ε select a random action aₜ
        Otherwise select aₜ = argmaxₐ Q(ϕ(sₜ), a; θ)

        Execute action aₜ in environment
        Observe reward rₜ and next state sₜ₊₁
        Preprocess next state: ϕₜ₊₁ = ϕ(sₜ₊₁)

        Store transition (ϕₜ, aₜ, rₜ, ϕₜ₊₁) in B
        Sample random minibatch of transitions (ϕᵢ, aᵢ, rᵢ, ϕᵢ₊₁) from B

        Set yᵢ =
            rᵢ                           if terminal state
            rᵢ + γ maxₐ' Q(ϕᵢ₊₁, a'; θ⁻) otherwise

        Perform gradient descent on
        (yᵢ - Q(ϕᵢ, aᵢ; θ))²
        with respect to network parameters θ

        Every C steps, reset θ⁻ = θ
    End For
End For
```

---

### Key Parameters
- `replay_buffer`: Stores past experiences to break temporal correlations.
- `Q_network`: The main network used for action selection and training.
- `Q_target_network`: A stable network used to compute target Q-values.
- `epsilon`: Exploration probability in the epsilon-greedy policy.
- `gamma`: Discount factor for future rewards.
- `batch_size`: Number of transitions sampled from the replay buffer.
- `target_update_frequency`: Frequency at which the target network is updated.

---

## References
- [Deep Q-Networks (DQN): Playing Atari with Deep Reinforcement Learning](https://arxiv.org/abs/1312.5602)
