---
title: "Crowd-FM: Learned Optimal Selection of Conditional Flow Matching-generated Trajectories for Crowd Navigation"
collection: publications
category: conferences
permalink: /publications/CrowdFM
excerpt: ''
date: 2026-06-01
venue: 'Accepted at the IEEE International Conference on Robotics and Automation(ICRA)'
slidesurl: ''
paperurl: ''
citation: 'Antareep Singha, Laksh Nanwani, Mathai Mathew P., Samkit Jain, P.T. Singamaneni, Arun Kumar Singh, K. Madhava Krishna.'

---

Safe and computationally efficient local planning for mobile robots in dense, unstructured human crowds remains a fundamental challenge. Moreover, ensuring that robot trajectories are similar to how a human moves will increase the acceptance of the robot in human environments. In this paper, we present Crowd-FM, a learning-based approach to address
both safety and human-likeness challenges. Our approach has two novel components. First, we train a Conditional FlowMatching (CFM) policy over a dataset of optimally controlled trajectories to learn a set of collision-free primitives that a robot can choose at any given scenario. The chosen optimal control solver can generate multi-modal collision-free trajectories, allowing the CFM policy to learn a diverse set of maneuvers. Secondly, we learn a score function over a dataset of human demonstration trajectories that provides a human-likeness score for the flow primitives. At inference time, computing the optimal trajectory requires selecting the one with the highest score. Our approach improves the state-of-the-art by showing that our CFM policy alone can produce collision-free navigation with a higher success rate than existing learning-based baselines. Furthermore, when augmented with inference-time refinement, our approach can outperform even expensive optimisation-based planning approaches. Finally, we validate that our scoring network can select trajectories closer to the expert data than a manually designed cost function.