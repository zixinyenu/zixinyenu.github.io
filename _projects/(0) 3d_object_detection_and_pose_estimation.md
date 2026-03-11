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
<img src="{{ site.url }}{{ site.baseurl }}/assets/det_pipeline.png"/>
<br>

**Inference server**<br>
The inference server is a ROS node that runs a deep learning model (CNN) to detect objects in the image space. The inference server is implemented in Python using [Detectron2](https://github.com/facebookresearch/detectron2) and Pytorch as the deep learning framework. For the use case of this project, a custom dataset is created to train the model. Mask-RCNN is used as the model architecture since we need to implement instance segmentation. The model was then trained with 100 self-labeled images with an ontology of a "cheez-it" box. The labeled images are shown below:
<br>
<img src="{{ site.url }}{{ site.baseurl }}/assets/annotation_results.gif"/>
<br>
The images are annotated on an open-sourced platform, [CVAT](https://github.com/opencv/cvat). CVAT provides many tools to accelerate the labeling processes and improve the qualities, such as machine learning models. 
<br>
The model was then trained using Detectron2 with 100 labeled images. The inference results are shown below:
<br>
<img src="{{ site.url }}{{ site.baseurl }}/assets/instance_segmentation.gif"/>
<br>
The inference server subscribes to the image topic and computes the target object masks. The inference server then publishes the masks to the perception core node.

**Perception core**<br>
The perception core is a ROS node that performs the following tasks:
* Receives both the point cloud from the LiDAR and the image from the RGB camera
* Detects the table in point cloud data and removes it
* Denoises, downsamples, and clusters the point cloud data to create a foreground mask
* Receives the target object masks from the inference server and gets a inference mask
* merge the foreground mask and the inference mask to get a final mask
* Performs oriented bounding box detection and pose estimation on the final mask with a state machine

The perception core is implemented in C++ using ROS. The node uses PCL for the point cloud process and OpenCV for the image process. The organized point cloud acquired from the realsense Lidar helped significantly reduce the perception core's runtime. The algorithms in the node were implemented to keep the organized point cloud using a customized data structure, **OrderedCloud**. Moreover, some algorithms were implemented in image space to reduce the runtime, such as **denoise**, **downsample**, and **cluster**. As a result, the node can be run efficiently with real-time performance. A state machine controls the detection and pose estimation processes based on the motion in the image space.

The below image shows the table removal process:
<br>
<img src="{{ site.url }}{{ site.baseurl }}/assets/background_remover.gif"/>
<br>

The below image shows the colorized point cloud clusters after denoising, downsampling, and clustering:
<br>
<img src="{{ site.url }}{{ site.baseurl }}/assets/cluster.gif"/>
<br>

The below image shows the CAD model replacement of the target objects:
<br>
<img src="{{ site.url }}{{ site.baseurl }}/assets/detection.gif"/>
<br>


### Future Scope 
* Implement a faster CNN model for instance segmentation such as [YOLACT-EDGE](https://github.com/haotian-liu/yolact_edge) to reduce the inference time
* Annotate more images to train a more robust and accurate model
* Annotate the model based on the cropped images to reduce the inference time
* Call the inference server with cropped images to reduce the inference time
* Implement a more robust and accurate pose estimation algorithm, such as point cloud registration
* Multi-thread CPU implementation on the perception core node to reduce the runtime
* Implement some OpenCV and PCL algorithms in GPU to reduce the runtime
