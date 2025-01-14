# DQN Application with Unity ML Agents for the Udacity's Deep Reinforcement Learning Nanodegree
## Project Details
In this project, the task is to train an agent to navigate and gather bananas within a large square environment (Banana.x86_64 from Unity ML-Agents)
The virtual environment consists of an animated scene featuring scattered yellow and blue objects resembling bananas. The agent earns a reward of +1 for collecting a yellow banana and a penalty of -1 for picking up a blue banana. Therefore, the agent's objective is to maximize its collection of yellow bananas while steering clear of the blue ones.
An example of the environment is show below:
![Ambiente](https://video.udacity-data.com/topher/2018/June/5b1ab4b0_banana/banana.gif)
The state space is represented by 37 dimensions, which include the agent's velocity and ray-based sensory input that detects objects in the agent's forward view. Using this data, the agent must learn to make the best decisions. There are four discrete actions available:
0: Move forward
1: Move backward
2: Turn left
3: Turn right
The task is episodic. To successfully solve the challenge, the agent must achieve an average score of +13 across 100 consecutive episodes.

## Getting Started
The README describes the the project environment details (i.e., the state and action spaces, and when the environment is considered solved).
## Instructions
The README describes how to run the code in the repository, to train the agent. For additional resources on creating READMEs or using Markdown, 
