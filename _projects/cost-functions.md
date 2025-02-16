---
title: "CrowdSurfer mapped to scene-specific cost functions for Social Navigation"
excerpt: "Learning to map CrowdSurfer's observation spcae to a social navigation rule set"
collection: projects
permalink: /projects/IROS25/
date: 2025-01-28
gif: group_interaction_behavior.gif
category: robotics
---

My work for IROS 2025 is to improve CrowdSurfer and integrate social behavior into it. This has been done by training a **Vision Transformer(ViT)** based classifier that maps the observation space of CrowdSurfer to a set of socially-compliant rules. The observation space includes:
 
- Occupancy maps  
- Dynamic obstacle positions  
- Static obstacle positions

The classifier outputs a softmax distribution over these rules, which are then mapped to a set of hand-tuned cost functions. Below is an example of one such cost function, **Group Interaction Cost**:

$$
C_{group}(x, y) = \sum_{j=1}^{M} \frac{1}{d_j + \epsilon}
$$

- **M**: Number of groups detected in the environment  
- **d<sub>j</sub>**: Distance to the centroid of the *j*-th group  
- **ε**: A small positive constant to avoid division by zero when *d<sub>j</sub>* is very small  

This cost ensures the ego-agent avoids passing through groups of people.

---

## Additional Cost Functions

### 1. Directional Alignment Cost

$$
C_{alignment}(x, y) = \sum_{t} \left( 1 - \cos\bigl(\theta_{agent,t} - \theta_{flow,t}\bigr) \right)
$$

Encourages socially compliant behavior by matching the direction of nearby pedestrians.

### 2. Yielding Cost

$$
C_{yielding} 
= w_y \cdot \sum_{j=1}^{m} \frac{\bigl(1 - P_{\text{priority}}(j)\bigr)}{d_j + \epsilon} 
\cdot \max\bigl(0, v_{j,\text{rel}} - v_{\text{threshold}}\bigr)
$$

- **Proximity Penalty** \(\frac{1}{d_j + \epsilon}\):  
  Closer obstacles contribute more to the cost, encouraging the agent to yield when obstacles are nearby.

- **Relative Velocity Contribution** \(\max(0, v_{j,\text{rel}} - v_{\text{threshold}})\):  
  The cost increases only if the relative velocity exceeds a predefined threshold \(v_{\text{threshold}}\). This ensures the agent responds to dynamic obstacles with significant motion differences.

- **Priority Weighting** \(\bigl(1 - P_{\text{priority}}(j)\bigr)\):  
  Obstacles with higher priority contribute less to the cost, encouraging the agent to yield to them.

---

## Features

- **Current Implementation**: Includes only *Group Interaction Cost*.  
- **ViT Training**: Conducted on a synthetic dataset of PEDSIM rosbags.

---

## Technologies Used

- **Optimal Control**  
- **Machine Learning**  
- **PyTorch**  
- **JAX**

---

> **Note**: The project repository is still under development and remains private.