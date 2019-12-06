# DRLND-P1 Report : Navigation

[//]: # "Image References"
[image0]: ./imgs/DQN.jpg "DQN"
[image1]: ./imgs/score_list.png "score list"
[image2]: ./imgs/scores.png "scores"
### Learning Algorithm

![alt_text][image0]

The learning algorithm is based on DQN and two main techniques are implemented : 

- Replay buffer : Use replay buffer to record experience tuples and train agent by sampling from it. 

- Fixed target : A skill to decouple temporal difference target from agent's actions. It helps build up a more stable learning environment.



### Implementation

The implementation is based on the DQN solution in `Lunar Lander` tutorial from Udacity Deep Reinforcement Learning Nanodegree with some modifications.

`model.py` describes the model architecture of Q-network. 

`dqn_agent.py` implements a DQN agent class `Agent()` and a replay buffer class `ReplayBuffer`.

- `Agent()` provide three methods `step()`, `act()`, and `learn()` for interacting and learning from the environment.
  - `__init__()` : Create local Q-network, target Q-network, replay buffer and initialize some parameters.
  - `act()` : Use local Q-network to select action (A) based on current state (S). Besides, the action selection follows epsilon-greedy action selection strategy.
  - `step()` : Save experience in replay memory based on current state (S), action selected (A), reward (R) obtained and next state (S') reached. Then call `learn()` method to update Q-network parameters based on random sampling subset samples in replay buffer periodically when there are enough samples.
  - `learn()` : Update Q-network weights based on sampled experience tuples from replay buffer. Then call `soft_update()` to update target Q-network weights softly.
  - `soft_update()` : Use a parameter `TAU` to control how much target Q-network weights are updated based on target Q-network weights and local Q-network weights.

- `ReplayBuffer` provide `add()` and `sample()` methods for adding experience tuple and randomly sample a bath of experiences from replay buffer

### Hyperparameters

```python
# DQN hyperparameters
max_t = 1000            # max time step for an episode
BUFFER_SIZE = int(1e5)  # replay buffer size
BATCH_SIZE = 64         # minibatch size
GAMMA = 0.99            # discount factor
TAU = 1e-3              # for soft update of target parameters
LR = 5e-4               # learning rate of Adam optimizer
UPDATE_EVERY = 4        # how often to update the network

## Epsilon-greedy
eps_start = 1.0
eps_end = 0.01
eps_decay = 0.995
```

For each episode, agent goes through 1000 time step `(max_t)`. The replay buffer size `BUFFER_SIZE` is 1e5 , the batch size `BATCH_SIZE` sampling from it is 64. 

The reward discount factor`GAMMA` is 0.99. For soft update target parameters, `TAU` controls how much target parameters are updated.

The learning rate `LR` of Adam optimizer for Q-network is 5e-4 and the network parameters are updated for every 4 time step `(UPDATE_EVERY)` when there are enough samples in replay buffer.

For epsilon-greedy action selection, epsilon is started as 1.0 `(eps_start)`and decays 0.995 `(eps_decay)` until 0.01 `(eps_end)` for each time step.

```python
# Q-Network architecture
(Input)  State (37 nodes)
(FC1)    Fully connected layer (64 nodes) + ReLU activation function
(FC2)    Fully connected layer (64 nodes) + ReLU activation function
(FC3)    Fully connected layer (64 nodes) + ReLU activation function
(Output) Action (4 nodes)
```

The Q-network are consists of 3 consecutive fully connected layer with 64 nodes and followed by ReLU activation function.

### Plot of Rewards

Based on the above implementation and parameter settings, **the trained agent can receive an average reward (over 100 episodes) of at least +13 (14.01) in 371 episodes** : 



![alt_text][image1]



![alt_text][image2]

### Ideas for Future Work

There are lots work can be tried in this project, such as 

- Use prioritized replay buffer : try to sample high reward tuple with a higher priority
- Use double DQN technique : because DQN tends to overestimate action values and leads to instability in the beginning training phase of DQN, double DQN technique can lessen this problem.