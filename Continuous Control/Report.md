[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/43851024-320ba930-9aff-11e8-8493-ee547c6af349.gif "Trained Agent"
[image2]: https://user-images.githubusercontent.com/10624937/43851646-d899bf20-9b00-11e8-858c-29b5c2c94ccc.png "Crawler"
[Paper DDPG ]: https://arxiv.org/pdf/1509.02971.pdf


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

Train 20 angels in more than 100 episodes in addition to the average training score exceeding 30

## Algorithm used: DDPG: Deep Deterministic Policy Gradient
[paper DDPG]

DDPG is a different type of Actor-Critical method, it could be like approximate DQN instead of a real critical actor. The reason for this is that the critical DDPG is used to approximate the maximizer on the Q values of the next state and not as a learned baseline.
One of the limitations of the DQN agent is that it is not easy to use in continuous action spaces.
In DDPG two deep neural networks are used: the actor and the critic; Where the actor is used to approximate the optimal policy in a deterministic way, this means that we always want to generate the best action believed for any given state.
This is different in stochastic policies in that we want the policy to learn a probability distribution on stocks.
At DDPG he seeks a deterministic policy; This means the best action believed every time we consult the network of actors. The actor is basically learning the best action and the critic learns to evaluate the optimal action value function.
    
## Agent implementation

To solve the problem use the DDPG agorithm implemented parameters of the original document, based on trial and error was changing some things, (too many tests and hours of training)
At the beginning I did not understand why my culva did not leave a score between 0-1 despite the number of episodes this did not change, I was changing the BUFER from 1e1 to 1e9 where the results and the graphics varied, initially I took 1000 epoch but the results were disastrous, it changed to start from something very low like 150 epoch and the thing changed, my score parameters were increasing, reaching as my maximum of 5 the average Score. I was alternated the random_seed and the results that reached me as a maximum of 19 (my greatest achievement after days). In the end, I achieved the expected results by playing with the DDPG hyperparameters, in addition to the fact that the actor had two hidden layers, both with relu-actiation and using the output of 1 unit + tanh activation; The critical model with 2 hidden layers (plus relu activation), a contact layer (with a size of actionspace (4)) and an output layer.
    
### DQN Hyperparameters used in this project

    BUFFER_SIZE = int(1e5)  # replay buffer size
    BATCH_SIZE = 128        # minibatch size
    GAMMA = 0.99            # discount factor
    TAU = 1e-3              # for soft update of target parameters
    UPDATE_EVERY = 1        # how many steps to take before updating target network
    LR_ACTOR = 1e-4         # learning rate of the actor 
    LR_CRITIC = 1e-4        # learning rate of the critic
    WEIGHT_DECAY = 0        # L2 weight decay


### Ideas for Future Work

    1. You could try different agents like PPO or A3C

 by @susyjam

