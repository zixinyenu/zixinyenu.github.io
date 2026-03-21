---
name: Reinforcement Learning Approach to Robot Navigation and Obstacle Avoidance
tools: [Python, ROS 2, Gazebo, Stable Baselines 3, Gymnasium]
image: https://zixinyenu.github.io/assets/me499/0_profile.gif
description: Designed a curriculum learning strategy, built a training pipeline to implement multiple reinforcement learning algorithms and trained a model to achieve robot navigation and obstacle avoidance.
---



# Reinforcement Learning Approach to Robot Navigation and Obstacle Avoidance
<br>



### Video demo
{% include elements/video.html id="yf98pt72DS0" %}
<br>



### Motivation
The deployment of mobile robots in real world is a challenging task, since the robots 
are expected to safely navigate themselves in new or dynamic environments, where perserving 
an explicit map can be impractical. Online pathfinding algorithms and SLAM algorithms have been 
developed and optimized for a long time to solve this challenge. While recent years have seen 
application of reinforcement learning recorded than any other time, the potential of applying RL 
on mobile robots cannot be easily neglected. Therefore, a RL approach to robot navigation and obstacle 
avoidance is presented in this project.
<br>



### Overview
This project aims to train a deep reinforcement learning model for TurbleBot 3 to perform navigation 
and obstacle avoidance in a random environment. A training framework based on curriculum learning strategy as well as a training pipeline in simulated environment have been developed to achieve this goal. It is assumed that no priori information about the environment is given to the robot, but only distance, relative bearing and lidar readings are accessible.
<br>



### Architecture
<br>



### Software
* ROS 2: An open-source robotics middleware suite which provides a set of software frameworks for robot software development.
* Gazebo: An open-source 3D robotics simulator.
* Stable Baselines 3: A set of reliable implementations of reinforcement learning algorithms in PyTorch. It is the latest major version of Stable Baselines, which is an improved version of OpenAI Baselines.
* Gymnasium: An API standard for reinforcement learning which helps create custom environment. It is a maintained fork of OpenAI’s Gym library.
<br>



### Training Strategy: Curriculum Learning
<br>
<br>

**Phase 1**
<br>
* Phase 1.1: 
<img src="{{ site.url }}{{ site.baseurl }}/assets/me499/0_p11.gif"/>
* Phase 1.2: 
<img src="{{ site.url }}{{ site.baseurl }}/assets/me499/0_p12.gif"/>
* Phase 1.3: 
<img src="{{ site.url }}{{ site.baseurl }}/assets/me499/0_p13.gif"/>
<br>

**Phase 2**
<br>
* Phase 2.1:
<img src="{{ site.url }}{{ site.baseurl }}/assets/me499/0_p21.gif"/>
* Phase 2.2:
<img src="{{ site.url }}{{ site.baseurl }}/assets/me499/0_p22.gif"/>
<br>

**Phase 3**
<img src="{{ site.url }}{{ site.baseurl }}/assets/me499/0_p3_map_gen.gif"/>
<br>
* Phase 3.1:
<img src="{{ site.url }}{{ site.baseurl }}/assets/me499/0_profile.gif"/>
<br>



### Future Scope 
1. Implement More RL Algorithms: Due to the time constraint of the winter quarter, the development on this project by this post so far only has a span of 10 weeks. Most of the models across Phase 1 to Phase 3 were trained with PPO, some of them were also trained with A2C. Stable Baselines 3 provides optimized implementation of a great number of RL algorithms, which should definitely be tried on this topic.
2. Deploy Trained Models on a Real TurtleBot3: The performance of trained models has only been verified in simulation. Model deployment on real robots is expected in the future.

### Citations
1. Dobrevski M, Skočaj D. Deep reinforcement learning for map-less goal-driven robot navigation. International Journal of Advanced Robotic Systems. 2021;18(1). doi:10.1177/1729881421992621
