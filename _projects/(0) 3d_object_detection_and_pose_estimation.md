---
name: Map-less, Goal-driven Navigation for TurtleBot 3 Based on Reinforcement Learning
tools: [Python, ROS 2, Gazebo, Stable Baselines 3, Gymnasium]
image: https://zixinyenu.github.io/assets/0_phase_3_training.gif
description: Designed a training framework for TurtleBot 3 navigation via reinforcement learning approach and built the training pipeline.
---

# Map-less, Goal-driven Navigation for TurtleBot 3 Based on Reinforcement Learning
<br>
### Project Description
<br>
Mobile robots deployed in real-world environments are expected to navigate reliably around
their surroundings. In static environments, a map could be built to help with the localization
and path-planning of the robot. However, in a new or dynamic environment where
preserving a map is not feasible, it is more appropriate to develop a map-less approach
which only relies on sensor readings.
<br><br>
This project aims to create a navigation model for TurtleBot1 robot via a reinforcement
learning approach. It is assumed that no priori information about the environment is given
to the robot, but only distance and relative bearing between the robot position and 
the goal position is provided along with lidar readings as the observation space.
<br>
### Video demo
<br>
TO BE ADDED.
<br>

### Software
* ROS 2: An open-source robotics middleware suite which provides a set of software frameworks for robot software development.
* Gazebo: An open-source 3D robotics simulator.
* Stable Baselines 3: A set of reliable implementations of reinforcement learning algorithms in PyTorch. It is the latest major version of Stable Baselines, which is an improved version of OpenAI Baselines.
* Gymnasium: An API standard for reinforcement learning which helps create custom environment. It is a maintained fork of OpenAI’s Gym library.

### Pipeline
<br>
<img src="{{ site.url }}{{ site.baseurl }}/assets/winter_project_diagram.drawio.png"/>
<br>


### Future Scope 
* Implement a faster CNN model for instance segmentation such as [YOLACT-EDGE](https://github.com/haotian-liu/yolact_edge) to reduce the inference time
* Annotate more images to train a more robust and accurate model
* Annotate the model based on the cropped images to reduce the inference time
* Call the inference server with cropped images to reduce the inference time
* Implement a more robust and accurate pose estimation algorithm, such as point cloud registration
* Multi-thread CPU implementation on the perception core node to reduce the runtime
* Implement some OpenCV and PCL algorithms in GPU to reduce the runtime
