[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/42135619-d90f2f28-7d12-11e8-8823-82b970a54d7e.gif "Trained Agent"
[paper]: https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf

# Project 1: Navigation
## Report


### Introduction

For this project, you will train an agent to navigate (and collect bananas!) in a large, square world.  

![Trained Agent][image1]

A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana.  Thus, the goal of your agent is to collect as many yellow bananas as possible while avoiding blue bananas.  

The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around agent's forward direction.  Given this information, the agent has to learn how to best select actions.  Four discrete actions are available, corresponding to:
- **`0`** - move forward.
- **`1`** - move backward.
- **`2`** - turn left.
- **`3`** - turn right.

The task is episodic, and in order to solve the environment, your agent must get an average score of +13 over 100 consecutive episodes.

## Objective

Collect as many yellow bananas as possible at any given time and avoid blue ones.
The agent has to find a banana next to him and move in that direction, prioritizing the yellow ones
It will be done on a two-dimensional plane despite the game being three-dimensional

### Algorithm used: Deep Q-Learning 

There are two processes that are intertwined in this algorithm

1. Take samples of the environment by performing actions and save the experienced and observed tuples in a repetition memory.
2. Randomly select a small batch of tuples in memory and learn from that batch using a gradient descent refresh step.

These processes do not depend directly on each other, so multiple sampling steps can be applied followed by learning

### Jacqueline susan Mejía C.

