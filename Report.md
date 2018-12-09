# Report

The goal of this project is to train two agents by deep reinforcement learning algorithms so that they can control rackets to bounce a ball over a net.

# Method

Multi-Agent Distributed Distributional Deep Deterministic Policy Gradients (MAD4PG) has been implemented, details can be find in report.md

## Hyperparamters

After exploring several combinations, values below for hyperparameters allow the agent to solve the problem in stable manner.

Hyperparameter | Value
--- | ---    
Batch size | 64
Gamma | 0.99
τ | 1e-2
LR_ACTOR | 1e-4
LR_CRITIC | 1e-4
WEIGHT_DECAY | 0
N_step | 7
UPDATE_EVERY | 6
Vmax | 0.7
Vmin | -0.7
N_ATOMS | 51




## Network Structures

### Actor

Layer | Dimension
--- | ---
Input | N x 24
Linear Layer, Leaky Relu | N x 256
Linear Layer, Leaky Relu | N x 2
Batchnormalization1D | N x 2
Tanh Output | N x 2

### Critic

Layer | Dimension
--- | ---
Input | N x 24
Linear Layer, Leaky Relu | N x 128
Linear Layer + Actor Output, Leaky Relu | N x (128 + 2)
Linear Layer, Leaky Relu | N x 128
Linear Layer | N x 51

## Training Results

Below are the number of episodes needed to solve the environment and the evolution of rewards per episode during training.

![alt text](https://github.com/kelvin84hk/DRLND_P3_collab-compet/blob/master/pics/mdd4pg.png)

Environment was solved in 8135 episodes with Average Score 0.52.

# Ideas for future work


1. Implementing Rainbow Algorithm [https://arxiv.org/pdf/1710.02298.pdf] which combines good features from different algorithms to form an itegrated agent.

2. Implementing parallel computing so that it is able to use multiple agents to train simultaneously. 
