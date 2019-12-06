# DRLND-P1 : DQN Navigation

### Project Details

This is my work for the [Udacity Deep Reinforcement Learning Nanodegree](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893) (DRLND) Project 1 : Navigation. The goal of this project is to train an agent using Deep Q-Networks (DQN) to navigate in a large, square virtual world and collect as many yellow bananas as possible while avoiding blue bananas. 

**Environment**

The virtual environment is provided by Udacity. It is similar, but not identical to [Unity ML-agents](https://github.com/Unity-Technologies/ml-agents) banana collector environment.

**Reward**

A reward of +1 is provided for collecting a yellow banana and a reward of -1 is provided for collecting a blue banana. 

**State space**

The state space has 37 dimensions that contains the agent's velocity, along with ray-based perception of objects around agent's forward direction. 

**Action space**

Given the state information, the agent has to learn to select best actions. The action space has 4 discrete actions corresponding to :

- **`0`** - move forward.
- **`1`** - move backward.
- **`2`** - turn left.
- **`3`** - turn right.

**Goal**

The task is episodic, and in order to solve the environment, the trained agent must **get an average score of +13 over 100 consecutive episodes.**



### Getting Started

1. Install and configure Python 3 / PyTorch environment as described in [Udacity deep reinforcement learning repository](https://github.com/udacity/deep-reinforcement-learning)

2. Clone this repository to a local folder.

3. Download Udacity banana collector environment from one of the links below based on your operating system:

   - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
   - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
   - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
   - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)

   (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

4. Place the file in the local repository which cloned from step 2, say in the `DRLND-P1-Navigation/` folder, and unzip (or decompress) the file. 



### Instructions

#### Train a agent

1.  Activate the conda environment `drlnd` as established in [Udacity deep reinforcement learning repository](https://github.com/udacity/deep-reinforcement-learning)
2. Open jupyter notebook `Navigation.ipynb`
3. Change kernel to `drlnd` in `Navigation.ipynb`
4. Execute code cells from step 1 to step 4 in `Navigation.ipynb`, and trained model will be saved in `checkpoint.pth` as the average score > +14.0.

#### Test the trained agent

Execute code cell in step 5, the trained agent  will be tested for 1 episode.

