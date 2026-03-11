---
name: Map-less, Goal-driven Navigation for TurtleBot 3 Based on Reinforcement Learning
tools: [Python, ROS 2, Gazebo, Stable Baselines 3, Gymnasium]
image: https://zixinyenu.github.io/assets/0_phase_3_training.gif
description: Designed a training framework for TurtleBot 3 navigation via reinforcement learning approach and built the training pipeline.
---

# Map-less, Goal-driven Navigation for TurtleBot 3 Based on Reinforcement Learning
<br>

### Project Description
Mobile robots deployed in real-world environments are expected to navigate reliably around
their surroundings. In static environments, a map could be built to help with the localization
and path-planning of the robot. However, in a new or dynamic environment where
preserving a map is not feasible, it is more appropriate to develop a map-less approach
which only relies on sensor readings.
<br>
This project aims to create a navigation model for TurtleBot1 robot via a reinforcement
learning approach. It is assumed that no priori information about the environment is given
to the robot, but only distance and relative bearing between the robot position and 
the goal position is provided along with lidar readings as the observation space.
<br><br>

### Video Demo
TO BE ADDED.
<br><br>

### Software
* ROS 2: An open-source robotics middleware suite which provides a set of software frameworks for robot software development.
* Gazebo: An open-source 3D robotics simulator.
* Stable Baselines 3: A set of reliable implementations of reinforcement learning algorithms in PyTorch. It is the latest major version of Stable Baselines, which is an improved version of OpenAI Baselines.
* Gymnasium: An API standard for reinforcement learning which helps create custom environment. It is a maintained fork of OpenAI’s Gym library.
<br><br>

### Pipeline
<img src="{{ site.url }}{{ site.baseurl }}/assets/winter_project_diagram.drawio.png"/>
<br><br>

### Training Framework
The training framework of this project can be explained in three phases as follows.
<br>

**Phase 1**
<img src="{{ site.url }}{{ site.baseurl }}/assets/0_phase_1_training.gif"/>
<br>
This is the first stage of the model training. Since the training pipeline as shown in the above figure
consists of a lot of various systems, sub-systems and communication between them, user should conduct 
intensive debugging and functionality varification before working on any complicated learning goal. In the Phase 1, the TurtleBot 3 is always spawned at (0.0, 0.0, 0.0) in the map frame with an orientation of 0.0, and the map is empty (has no obstacles). It is going to learn to navigate to a randomly generated 
goal position which could be anywhere in the map, with a tolerance of 0.25 meters. The model gained in this phase will be used as a base model and be retrained in the following Phase Two.
* Phase 1.1: A goal position of (1.5, 0.0, 0.0) is given for every episode of training. Finishing this sub-phase will prove the training pipeline has no fundamental errors or bugs.
* Phase 1.2: Eight goal positions on a circle of raidus 1.5 meters centered at the turtle's spawning position is given with an equal probability for every episode of training. Finishing this sub-phase will prove the training pipeline is bug-free and designed in a generally good manner.
<img src="{{ site.url }}{{ site.baseurl }}/assets/0_phase_1_2_outcome.gif"/>
* Phase 1.3: Anywhere on the map within the fences could be given as the goal position for every episode of training. Finishing this sub-phase will yield a base motion model for the following phase.
<img src="{{ site.url }}{{ site.baseurl }}/assets/0_phase_1_3_outcome.gif"/>
<br>

**Phase 2**
This is the second phase of the model training. A good motion model has been trained from last phase, which issues twist commands to navigatie the TurtleBot 3 to reach any goal position in a obstacle-free environment. Now obstacles will be added as a part of the training environment. The robot is still spawn at the origin of the map frame with orientation of 0.0, and obstalces will be added right on a straight line from the robot to the goal position. In Phase 2 all the environment settings except goal position is fixed for every episode, which means the randomness is relatively constrained. The robot will learn basic obstacle avoidance, and the model gained from this phase will be used as the base model for Phase 3.
* Phase 2.1: TO DO
* Phase 2.2: TO DO
* Phase 2.3: TO DO
<br>

**Phase 3**
This is the third phase of the model training. A model with good navigation and basic obstacle avoidance has been trained from last phase. Now more randomness is introduced to the training environment. The TurtleBot 3 could be spawned at any location on the map with any possible orientation. There are different numbers of obstacles with different sizes, locations and orientations for eacho episode. The goal position also could be any empty spot on the map.
* TO DO
<br>
<img src="{{ site.url }}{{ site.baseurl }}/assets/0_phase_3_training.gif"/>
<br><br>


### Future Scope 
* 
