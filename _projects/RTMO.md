---
title: "Real-Time Human Body Pose Estimation using RTMO"
excerpt: "Body Pose Estimation pipeline using RealSense D455 to be integrated with CrowdSurfer"
collection: projects
permalink: /projects/rtmo/
date: 2024-10-20
gif: body_pose.gif
category: robotics
---

I wanted to train CrowdSurfer on social cues including the body pose of a human obstacle. The idea was that if a human is looking at the robot, there are high chances that they will avoid it and the robot does not have to do anything in such a situation. Only, when the human is unaware of the robot(they are not facing directly toward the robot), the robot has to avoid the human. This can save a lot of computation and the planning does not have to happen at a very high frequency at every timestep. Now how do we know if the human is directly facing toward the robot? Mapping their face orientation in space time is not a very good indicator because humans sometimes being in awe of fancy gizmos(like robots) keep looking at them while going in a completely different direction. I decided that the body-pose would be the perfect way to move forward becuase that is what stays constant with the direction the human is moving.

This pipeline finds out the body pose using RTMO. RTMO is a CVPR 2024 paper that achieves performance comparable to RTMPose. I use the keypoints outputted by RTMO and use the shoulder and nose keypoints to find out the cross-product. The cross-product gives the body-pose of the human.


## Technologies Used

- Python
- Computer Vision
- ROS Noetic

[Link to Project Source Code](https://github.com/MysEcho/RRC-Misc/blob/main/body-pose.py)\
[View the project on YouTube](https://www.youtube.com/watch?v=Oyhp_HQT1aQ)