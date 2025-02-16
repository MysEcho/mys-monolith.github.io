---
title: "CrowdSurfer mapped to scene-specific cost functions for Social Navigation"
excerpt: "Learning to map CrowdSurfer's observation spcae to a social navigation rule set"
collection: projects
permalink: /projects/IROS25/
date: 2025-01-28
gif: group_interaction_behavior_comparison.gif
category: robotics
---

My work for IROS 2025 is to improve CrowdSurfer and integrate social behavior into it. This has been done by training a Vision Transformer(ViT) based classifier that maps the observation space of CrowdSurfer to a set of socially-compliant rules. The observation space includes occupancy maps, dynamic and static obstacle positions. The classifier predicts a softmax over all these rules. These rules are then mapped to a set of hand-tuned cost functions. For the example here, the cost modeled is "Group Interaction Cost".
$$
C_{group}(x, y) = \sum_{j=1}^{M} \frac{1}{d_j + \epsilon}
$$

M: Number of groups detected in the environment  
dj: Distance to the centroid of the j-th group
ϵ: A small positive constant to avoid division by zero when dj is very small.  

This cost ensures that the ego-agent avoids passing through groups of people.

Other cost functions include:

i. Directional Alignment Cost:
$$
C_{alignment}(x, y) = \sum_{t} \left( 1 - \cos\bigl(\theta_{agent,t} - \theta_{flow,t}\bigr) \right)
$$

This cost is supposed to encourage socially compliant behavior by matching the direction of nearby pedestrians.

ii. Yielding Cost:

$$
C_{yielding} 
= w_y \cdot \sum_{j=1}^{m} \frac{\bigl(1 - P_{\text{priority}}(j)\bigr)}{d_j + \epsilon} 
\cdot \max\bigl(0, v_{j,\text{rel}} - v_{\text{threshold}}\bigr)
$$

Proximity Penalty (1/(dj+ϵ)) - Closer obstacles contribute more to the cost, encouraging the agent to yield when obstacles are nearby.

Relative Velocity Contribution (max(0,vj,rel−vthreshold)) - The cost increases only if the relative velocity exceeds a predefined threshold, vthreshold. This ensures the agent responds to dynamic obstacles with significant motion differences. 

Priority Weighting (1−Ppriority(j)) - Obstacles with higher priority contribute less to the cost, encouraging the agent to yield to them.

## Features

- Current implementation only has a single static obstacle constraint.
- Rollout time for Acados was 20 milliseconds whereas for CasADi was around 90 milliseconds.
- Can be integrated in the future for deployment.

## Technologies Used

- Optimal Control
- Machine Learning
- PyTorch
- JaX

## NOTE:

Project Repository is still under development and thus private.