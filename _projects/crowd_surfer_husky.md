---
title: "CrowdSusrfer on Husky(without Global Plan)"
excerpt: "CrowdSurfer in Action on Clearpath Husky A200 Prototype with pure local planning"
collection: projects
permalink: /projects/crowd_surfer-husky/
date: 2024-10-20
gif: Husky_2.gif
category: robotics
---

CrowdSurfer is a Path Planning Algorithm that is built on top of the Sampling based optimizer called PRIEST(our previous work). CrowdSurfer makes use of a Vector Quantized VAE to generate a distribution diverse motion primitives for PRIEST to sample from. The VQVAE model is trained by Behavior Cloning using Expert Demonstrations of a wheelchair navigating in extremely crowded environments. 

This work has been submitted to IEEE ICRA 2025 and is currently under review.

## Features

- Multi-modal in nature.
- Can navigate in extremely crowded environments with more than 50 humans.
- Excellent run-time speeds of 40ms per trajectory rollout.

## Technologies Used

- Generative Modeling (VQ-VAE + PixelCNN)
- Batch Optimization
- ROS Nav Stack

[Link to Project Repository](https://github.com/yourusername/project-repo)\
[View the project on YouTube](https://www.youtube.com/watch?v=KdJvIh54vG0)