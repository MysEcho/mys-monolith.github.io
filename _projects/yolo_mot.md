---
title: "Multiple Object Tracking using YOLOv8"
excerpt: "This is an implementation of Open-set multiple object tracking using YOLOv8"
collection: projects
permalink: /projects/yolo/
date: 2024-10-20
gif: YOLO_mot.gif
category: robotics
---

The title is self explanatory. I made this project as a part of our data collection pipeline for CrowdSurfer. CrowdSurfer required a lot of data and we decided to collect all the data using our custom wheelchair inside the IIIT Hyderabad campus. MOT using YOLOv8 works with an open-set, meaning it detects any obstacle with a relatively high degree of confidence. I made a ROS implementation so that it can easily work with the other components of the stack.

## Features

- Open-Set
- Interfaced with RealSense D455 ROS
- High degree of confidence

## Technologies Used

- Computer Vision
- PyTorch
- ROS Noetic

[Link to Project Source Code](https://github.com/MysEcho/RRC-Misc/blob/main/YOLO_RealSense.py)\
[View the project on YouTube](https://www.youtube.com/watch?v=aRSqPu45gjA)