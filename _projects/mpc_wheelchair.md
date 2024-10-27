---
title: "Model Predictive Control Stack on Autonomous Wheelchair"
excerpt: "Our custom MPC stack is built on top of IPOPT using the CasADi symbolic framework."
collection: projects
permalink: /projects/mpc-wheelchair/
date: 2024-10-20
gif: MPC_final.gif
category: robotics
---

The Model Predictive Control for our Autonomous Wheelchair uses IPOPT(Interior Point Optimization) with constraint to linearly extrapolated dynamic obstacle velocities. The velocities are obtained from an ICRA 2015 paper called "Leg Tracker" by Angus Leigh et. al. 

## Features

- Takes in consideration dynamic obstacle velocities. This feature is absent from other classical methods like DWA, RRT*, MPPI etc.
- Very Robust and excellent run-time speed.
- Does not require Camera. Both Localization and Dynamic obstacle tracking can be done using a 2D LiDAR.

## Technologies Used

- Optimal Control
- CasADi
- ROS Noetic

[Link to Project Repository](https://github.com/yourusername/project-repo)