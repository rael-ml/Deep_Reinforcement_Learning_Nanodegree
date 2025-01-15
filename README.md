# DQN Application with Unity ML Agents for the Udacity's Deep Reinforcement Learning Nanodegree
## Project Details
In this project, the task is to train an agent to navigate and gather bananas within a large square environment (Banana.x86_64 from Unity ML-Agents).

The virtual environment consists of an animated scene featuring scattered yellow and blue objects resembling bananas. The agent earns a reward of +1 for collecting a yellow banana and a penalty of -1 for picking up a blue banana. Therefore, the agent's objective is to maximize its collection of yellow bananas while steering clear of the blue ones

An example of the environment is shown below:

![Ambiente](https://video.udacity-data.com/topher/2018/June/5b1ab4b0_banana/banana.gif)

The state space is represented by 37 dimensions, which include the agent's velocity and ray-based sensory input that detects objects in the agent's forward view. Using this data, the agent must learn to make the best decisions. There are four discrete actions available:
0: Move forward
1: Move backward
2: Turn left
3: Turn 

The task is episodic. To successfully solve the challenge, the agent must achieve an average score of +13 across 100 consecutive episodes.

##  Files

- **Navigation.ipynb:** Jupyter Notebook with the DQN Agent that explores the Banana environment.
- **README.md:** File explaining how to navigate through this project.
- **checkpoint.pth:** Saved weights of the DQN Network that can solve the environment.
- **requirements.txt:** The python libraries and the corresponding versions that are needed to run the project.
- **setup.py:** A python file that sets up the installation for the Unity Machine Learning Agents library, specifying its dependencies, metadata, and description for easy installation and usage.
- **Report.pdf:** A report file that contains a description of the learning algorithm, hiperparameters used and ideas for future works. 


## Getting Started
To run the code, first you need to download the Banana environment available in the links below:
For this project, you will not need to install Unity - this is because we have already built the environment for you, and you can download it from one of the links below. You need only select the environment that matches your operating system:

Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip).

Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip).

Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip).

Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip).

Then, place the file in the project folder, and unzip (or decompress) the file.



## Instructions
The code is avalable in the Navigation.ipyng notebook. First you need to run the following line:

<pre> python  !pip -q install . </pre>

This line of code will call "setup.py" and install the python librarys in requirements.txt

After this step, please restart the kernel to run the rest of the code.
