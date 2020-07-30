[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/43851024-320ba930-9aff-11e8-8493-ee547c6af349.gif "Trained Agent"
[image2]: https://user-images.githubusercontent.com/10624937/43851646-d899bf20-9b00-11e8-858c-29b5c2c94ccc.png "Crawler"


# Project 2: Continuous Control

### Introduction

For this project, you will work with the [Reacher](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher) environment.

![Trained Agent][image1]

In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of your agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

#### Option 2: Solve the Second Version

The barrier for solving the second version of the environment is slightly different, to take into account the presence of many agents.  In particular, your agents must get an average score of +30 (over 100 consecutive episodes, and over all agents).  Specifically,
- After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent.  This yields 20 (potentially different) scores.  We then take the average of these 20 scores. 
- This yields an **average score** for each episode (where the average is over all 20 agents).

The environment is considered solved, when the average (over 100 episodes) of those average scores is at least +30. 

## Objective

Collect as many yellow bananas as possible at any given time and avoid blue ones.
The agent has to find a banana next to him and move in that direction, prioritizing the yellow ones
It will be done on a two-dimensional plane despite the game being three-dimensional

## Algorithm used: Deep Q-Learning
[paper]

There are two processes that are intertwined in this algorithm

1. Take samples of the environment by performing actions and save the experienced and observed tuples in a repetition memory.
2. Randomly select a small batch of tuples in memory and learn from that batch using a gradient descent refresh step.

These processes do not depend directly on each other, so multiple sampling steps can be applied followed by learning.
    
## Agent implementation

For the implementation, DQN was used in its basic version mentioned in the Q-Learning lesson in addition to dqn_agent.py and model.py, which works quite well for training. DQN has two upper layers of 64 units each adomea of the RELU activation and a lost MSE.
The following was observed: the maximum average score (last 100) after enough training episodes and the time it took to reach the threshold of 13 points in the average score.

    eps_start=1.0, eps_end=0.01, eps_decay=0.995
  	Environment solved in 390 episodes!	Average Score: 13.03
  	scores leveled out @ ~ 11,0 (2000 episodes)
    
### DQN Hyperparameters used in this project

    BUFFER_SIZE = int(1e5)        # replay buffer size
    BATCH_SIZE = 64               # minibatch size
    GAMMA = 0.99                  # discount factor
    TAU = 1e-3                    # for soft update of target parameters
    LR = 5e-4                     # learning rate 
    UPDATE_EVERY = 4              # how often to update the network

### Ideas for Future Work

    1. I could try the Double DQN and see what changes exist regarding that model
    2. Could implement Rainbow-Version of DQN.
    3. Could implement CNN architecture to learn tha value- Function

 by @susyjam

