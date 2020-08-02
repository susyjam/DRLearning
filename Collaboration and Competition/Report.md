[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/42135623-e770e354-7d12-11e8-998d-29fc74429ca2.gif "Trained Agent"
[image2]: https://user-images.githubusercontent.com/10624937/42135622-e55fb586-7d12-11e8-8a54-3c31da15a90a.gif "Soccer"


# Project 3: Collaboration and Competition

### Introduction

For this project, you will work with the [Tennis](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#tennis) environment.

![Trained Agent][image1]

In this environment, two agents control rackets to bounce a ball over a net. If an agent hits the ball over the net, it receives a reward of +0.1.  If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01.  Thus, the goal of each agent is to keep the ball in play.

The observation space consists of 8 variables corresponding to the position and velocity of the ball and racket. Each agent receives its own, local observation.  Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping. 

The task is episodic, and in order to solve the environment, your agents must get an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents). Specifically,

- After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent. This yields 2 (potentially different) scores. We then take the maximum of these 2 scores.
- This yields a single **score** for each episode.

The environment is considered solved, when the average (over 100 episodes) of those **scores** is at least +0.5.

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
