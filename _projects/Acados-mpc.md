---
title: "Model Predictive Control Simulation using Acados"
excerpt: "This implementation of MPC uses Acados instead of CasADi for a single static obstacle."
collection: projects
permalink: /projects/mpc-acados/
date: 2024-04-14
gif: Acados_MPC.gif
category: robotics
---

The Model Predictive Control for our Autonomous Wheelchair uses IPOPT(Interior Point Optimization) with constraint to linearly extrapolated dynamic obstacle velocities. The velocities are obtained from an ICRA 2015 paper called "Leg Tracker" by Angus Leigh et. al. 

This implementation of MPC is using Acado whose backend is C++ and thus it is computationally much faster than CasADi. I developed this pipeline as a sanity check for our wheelchair but eventually the CasADi pipeline was preferred due to code readability and ease of use. I have made it open-source for anyone to use.

## Features

- Current implementation only has a single static obstacle constraint.
- Rollout time for Acados was 20 milliseconds whereas for CasADi was around 90 milliseconds.
- Can be integrated in the future for deployment.

## Technologies Used

- Optimal Control
- Acados
- C++

[Link to Project Repository](https://github.com/MysEcho/Acados-mpc)\
[View the project on YouTube](https://www.youtube.com/watch?v=HZDLmlqyj7Q)